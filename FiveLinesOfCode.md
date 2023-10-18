# Five Lines of Code
## Lange Funktionen zerschlagen
### Regel: »Fünf Zeilen«
***Feststellung***   

Eine Methode sollte nicht mehr als fünf Zeilen enthalten, ausgenommen Zeilen, die nur eine geschweifte Klammer, also `{` oder `}`, enthalten.

***Geruch***

Eine lange Methode riecht schon von selbst schlecht, weil man nur schwer mit ihr arbeiten kann. Man muss die Logik der gesamten Methode auf einmal im Kopf haben. 

### Refactoring: »Methode extrahieren«
***Beschreibung***

»Methode extrahieren« nimmt einen Teil einer Methode und macht daraus eine neue Methode. Das ist ein rein mechanischer Vorgang, und moderne IDEs können dieses Refactoring automatisch durchführen. Allein daruch ist es vermutlich sicher; Computer machen bei solchen Dingen selten Fehler. Man kann das Refactoring aber auch sicher von Hand ausführen.

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

***Geruch***

Die Aussage »Der Inhalt einer Funktion sollte auf derselben Abstraktionsebene bleiben« ist so wichtig, dass es ein eigner Code Smell ist. Wie die meisten Gerüche ist auch dieser schwer zu quantifizieren und noch schwieriger zu bekämpfen. Es ist aber sehr einfach zu erkennen, wenn etwas als Argument übergeben wird, und ebenso einfach ist es, wenn etwas vor einem Punkt steht.


### Regel: »›if‹ nur am Anfang«
***Feststellung***

Wenn es eine `if`-Anweisung gibt, dann sollte sie ganz am Anfang der Funktion stehen.

***Geruch***

Diese Regel - wie auch »Fünf Zeilen« - soll den Geruch verhindern, dass eine Funktion mehrere Verantwortlichkeiten hat. 

## Typen richtig nutzen
### Regel: »Benutze niemals ›if‹ mit ›else‹«
***Feststellung***

Benutze niemals `if` mit `else`, außer wenn du mit Typen arbeitest, die du nicht selbst kontrollierst.
### Refactoring: »Typcodes durch Klassen ersetzen«
### Refactoring: »Code in Klassen schieben«
### Refactoring: »Methode integrieren«
### Refactoring: »Methode spezialisieren«
### Regel: »Benutze niemal ›switch‹«
***Feststellung***

Benutze niemals `switch`, es sei denn, es gibt keinen `default`-Fall und *jeder* `case` hat eine `return`.
### Regel: »Erbe nur von Interfaces«
***Feststellung***

Erbe nur von Interfaces.
### Refactoring: »Versuchsweise löschen und kompilieren«
## Ähnlichen Code zusammenführen
### Refactoring: »Ähnliche Klassen zusammenführen«
### Refactoring: »›if‹s zusammenführen«
### Regel: »Benutze reine Bedingungen« 
***Feststellung**

Bedingungen sollten immer rein sein.
### Refactoring: »Strategie einführen«
### Regel: »Keine Interfaces mit nur einer Implementierung«
***Feststellung***

Es sollte keine Interfaces mit nur einer Implementierung geben.
### Refactoring: »Interface aus Implementierung extrahieren«
## Die Daten verteidigen
### Regel: »Benutze keine Getter und Setter«
***Feststellung***

Benutze keine Getter und Setter, außer für boolesche Felder.  
***Geruch***

Diese Regel leitet isch vom sogenannten *Gesetz der Demeter* ab, das gerne mit »Sprich nicht mit Fremden« paraphrasiert wird. Der Fremde in diesem Kontext ist ein Objekt, auf das wir keinen direkten Zugriff haben, aber auf das wir eine Referenz bekommen können. In objektorientierten Sprachen erhalten wir diese Referenz meist durch den Aufruf eines Getters - und deswegen gibt es diese Regel.

### Refactoring: »Getter und Setter löschen«
### Regel: »Vermeide gemeinsame Affixe«
### Refactoring: »Daten kapseln«
### Refactoring: »Reihenfolge erzwingen«
