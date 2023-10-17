# Five Lines of Code
## Lange Funktionen zerschlagen
### Regel: »Fünf Zeilen«
***Feststellung***   

Eine Methode sollte nicht mehr als fünf Zeilen enthalten, ausgenommen Zeilen, die nur eine geschweifte Klammer, also { oder }, enthalten.
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
***Feststellung***  

Eine Funktion sollte entweder Methoden an einem Objekt aufrufen oder das Objekt als Argument übergeben, aber nicht beides.
### Regel: »›if‹ nur am Anfang«
***Feststellung***

Wenn es eine ```if```-Anweisung gibt, dann sollte sie ganz am Anfang der Funktion stehen.
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
