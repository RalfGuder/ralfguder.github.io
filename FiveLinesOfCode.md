# Five Lines of Code
## Lange Funktionen zerschlagen
### Regel: »Fünf Zeilen«
``` TypeScript
function draw() {
  let canvas = document.getElementById("GameCanvas") as HTMLCanvasElement;
  let g = canvas.getContext("2d");

  g.clearRect(0, 0, canvas.width, canvas.height);

  // Draw map
  for (let y = 0; y < map.length; y++) {
    for (let x = 0; x < map[y].length; x++) {
      if (map[y][x] === Tile.FLUX)
        g.fillStyle = "#ccffcc";
      else if (map[y][x] === Tile.UNBREAKABLE)
        g.fillStyle = "#999999";
      else if (map[y][x] === Tile.STONE || map[y][x] === Tile.FALLING_STONE)
        g.fillStyle = "#0000cc";
      else if (map[y][x] === Tile.BOX || map[y][x] === Tile.FALLING_BOX)
        g.fillStyle = "#8b4513";
      else if (map[y][x] === Tile.KEY1 || map[y][x] === Tile.LOCK1)
        g.fillStyle = "#ffcc00";
      else if (map[y][x] === Tile.KEY2 || map[y][x] === Tile.LOCK2)
        g.fillStyle = "#00ccff";

      if (map[y][x] !== Tile.AIR && map[y][x] !== Tile.PLAYER)
        g.fillRect(x * TILE_SIZE, y * TILE_SIZE, TILE_SIZE, TILE_SIZE);
    }
  }

  // Draw player
  g.fillStyle = "#ff0000";
  g.fillRect(playerx * TILE_SIZE, playery * TILE_SIZE, TILE_SIZE, TILE_SIZE);
}
```
### Refactoring: »Methode extrahieren«
***Vorgehen***
1. Markiere die Zeilen, die du extrahieren willst, indem du sie mit Leerzeilen abgrenzt und ggf. durch einen Kommentar, der erklärt, was dieser Bereich tut.
2. Erzeuge eine neue, leere Methode mit dem gewünschten Namen.
3. Füge am Angang des markierten Bereichs einen Aufruf der neuen Methode ein.
4. Wähle alle Zeilen des Bereichs aus, schneide sie aus und füge sie in der neuen Methode ein.
5. Komiliere.
6. Führe in der neuen Methode Parameter ein, um die Fehler zu beheben.
7. Wenn wir *einem* der Parameter (nennen wir ihn p) einen neuen Wert zuweisen, dann  
   a. füge ```return p;``` als letzte Zeile der neuen Methode ein und
   b. schreibe den Aufruf als ```p = neueMethode();```.
8. Kompiliere.
9. Übergib beim Aufruf Argumente, um die Fehler zu beheben.
10. Entferne jetzt überflüssige Leerzeilen und Kommentare.


### Regel: »Aufrufen oder Übergeben«
### Regel: »›if‹ nur am Anfang«
## Typen richtig nutzen
### Regel: »Benutze niemals ›if‹ mit ›else‹«
### Refactoring: »Typcodes durch Klassen ersetzen«
### Refactoring: »Code in Klassen schieben«
### Refactoring: »Methode integrieren«
### Refactoring: »Methode spezialisieren«
### Regel: »Benutze niemal ›switch‹«
### Regel: »Erbe nur von Interfaces«
### Refactoring: »Versuchsweise löschen und kompilieren«
## Ähnlichen Code zusammenführen
### Refactoring: »Ähnliche Klassen zusammenführen«
### Refactoring: »›if‹s zusammenführen«
### Regel: »Benutze reine Bedingungen« 
### Refactoring: »Strategie einführen«
### Regel: »Keine Interfaces mit nur einer Implementierung«
### Refactoring: »Interface aus Implementierung extrahieren«
## Die Daten verteidigen
### Regel: »Benutze keine Getter und Setter«
### Refactoring: »Getter und Setter löschen«
### Regel: »Vermeide gemeinsame Affixe«
### Refactoring: »Daten kapseln«
### Refactoring: »Reihenfolge erzwingen«
