
# `converter.exe` – Middleware zur Fernsteuerung externer Software per Kommandozeile

## 🧭 Überblick

`converter.exe` ist eine .NET-basierte Middleware, die eine externe Software (z. B. RIB iTWO) per Kommandozeilenkommandos fernsteuert. Die Software nutzt XML-basierte Steuerdateien, die sequentiell verarbeitet werden, und unterstützt sowohl Einzel- als auch Batchbetrieb. Erweiterungen erfolgen modular über ein Plugin-System.

---

## 🚀 Aufrufmodi & Startparameter

### 1. Einzelkommando
```bash
converter.exe Export --input-file in.xml --output-file out.xml --status-file status.xml
```

### 2. Batch-Betrieb über Konfiguration
```bash
converter.exe --config config.xml
```

### 3. Unterstützte Startparameter (global)

| Parameter | Beschreibung |
|----------|--------------|
| `--config <file>` | XML-Datei mit Kommandoabfolge |
| `<CmdName>` | Einzelkommando |
| `--input-file`, `--output-file`, `--status-file` | Dateien für Einzelkommandos |
| `--start-file <file>` | Übergabe-Dateiname an Zielsoftware (wird nicht validiert) |
| `--fail-on-missing-plugin true|false` | Abbruch bei fehlendem Plugin (Default: true) |
| `--dry-run` | Testlauf ohne echte Ausführung |
| `--var KEY=VALUE` | Setzt/überschreibt Laufzeitvariablen |
| `--disable-variable-overwrite` | Verhindert Laufzeitänderungen von Variablen |
| `--log-file-level DEBUG|INFO|WARN|ERROR` | Loglevel Datei |
| `--log-console-level DEBUG|INFO|WARN|ERROR` | Loglevel Konsole |
| `--version <value>` | Version der Zielsoftware (Fallback zu ARR_REGVER) |
| `--list-commands` | Zeigt verfügbare Plugins an |
| `--help` / `<Cmd> --help` | Hilfeanzeige global oder kommandospezifisch |

---

## 🔧 Plugin-Architektur

- Plugins liegen im Ordner `./Modules`
- Nur .NET Framework 4.8-kompatibel, keine Drittabhängigkeiten
- Jedes Plugin implementiert `IModule` aus `Converter.Core.Modules`
- Eine DLL kann mehrere Plugins enthalten

### Interface `IModule`
```csharp
public interface IModule
{
    string Command { get; }
    string Description { get; }
    ILogService Logger { get; set; }
    IDictionary<string, string> ParameterMapper { get; }
    int Execute(IConfigurationSection config, IBaselineServicesAdapter service, ILogService logger, IEventBusService eventBus);
    List<string> Validate(IConfigurationSection config);
}
```

---

## 🧾 Konfigurationsdatei (`config.xml`)

### Beispielstruktur:
```xml
<configuration>
  <Section1>
    <Cmd>Export</Cmd>
    <InputFile>input.xml</InputFile>
    <OutputFile>export.gaeb</OutputFile>
    <StatusFile>Status.xml</StatusFile>
  </Section1>
</configuration>
```

- Platzhalter wie `${ExportPath}` oder `$(File1)` werden dynamisch ersetzt
- Variablenquellen: `config.xml`, `Converter.RIBConnector`, `--var`

---

## 🧠 Variablenverarbeitung

- Alle Variablen werden zentral verwaltet
- Reihenfolge:
  1. `Converter.RIBConnector`
  2. `config.xml`
  3. `--var`
- Nur Middleware darf Werte ändern
- Plugins können keine Variablen direkt manipulieren

---

## ❗ Fehlerverhalten

- Jeder Validierungsfehler (via `Validate`) → sofortiger Abbruch
- Exit-Codes:
  - `0`: Erfolg
  - `1`: Validierungs-/Ausführungsfehler
  - `2`: Fehlendes Plugin (bei `--fail-on-missing-plugin=true`)
  - `3`: Syntax-/Konfigurationsfehler

---

## 🪵 Logging

- Ausgabe in Konsole + Datei
- Log-Level getrennt konfigurierbar
- Standard-Logdatei: `Protocol.log`

---

## 📘 Hilfe & Diagnose

- `converter.exe --help`: Übersicht aller Startparameter
- `converter.exe <Cmd> --help`: Kommandohilfe
- `converter.exe --list-commands`: Auflistung aller geladenen Plugins (Level INFO)

---

## 📂 Startdatei (`--start-file`)

- Nur Pfad wird an Zielsoftware übergeben
- Middleware prüft **nicht**, ob Datei erstellt wurde
- Verantwortung liegt bei Zielsystem

---

## 📡 Ereignissystem (`IEventBusService`)

- Plugins können beliebige Events publizieren
- Middleware stellt Bus via `Publish<T>()` bereit
- Kein fester Nachrichtentyp vorgeschrieben

---

## ✅ Testplan

### Funktional
- Einzel- & Batchverarbeitung
- Platzhalterauflösung
- Logging & Eventausgabe
- Plugin-Erkennung

### Fehlerfälle
- Fehlendes Plugin
- Ungültige XML-Konfiguration
- Validierungsfehler

### Verhalten
- Logging getrennt nach Konsole/Datei
- Ereignisse bei Fortschritt/Warnung

---

© dotnet Services GmbH 2025
