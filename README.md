
# Übung 20 - Testvorbereitung


## 1. Aufgabe

Setzen Sie folgendes Klassendiagramm um:

<p align="center">
  <img src="/assets/images/UML1.png" alt="Bildbeschreibung" />
</p>

**Beschreibung der `Sitzplatz`-Klasse:**

- Eigenschaften: 
	- Im Konstruktor müssen die `set`-Methoden aufgerufen werden. 
	- `sitzplatz` darf nur die Werte `VIP` und `Standard` annehmen.
	- Hinweis: Sie dürfen davon ausgehen, dass `sitzPlatzNr` eindeutig ist. Sie müssen dies auch nicht überprüfen. 

- Methoden: 
	- `reservieren()`: Der Sitzplatz wird reserviert. Dies geht jedoch nur, wenn der Sitzplatz auch verfügbar ist. Kann der Sitzplatz reserviert werden, wird `true` zurückgegeben, sonst `false`. 
	- `stornieren()`: Der Sitzplatz wird storniert. Dadurch ist er wieder verfügbar.
	- `toString()`: Überschreiben Sie die `toString()`-Methode. Geben Sie einen String zurück, welcher alle Eigenschaften beinhaltet. 

**Beschreibung der `Raum`-Klasse:**
- Eigenschaften: 
	- Der Konstruktor soll `sitzplaetze` mit 5 Zeilen und  3 Spalten erzeugen und die `set`-Methode der `raumNr` Eigenschaft enthalten. 
	- `raumNr` muss als erstes Zeichen einen großen Buchstaben haben und danach muss eine Zahl folgen. 
- Methoden:
	- `sucheTyp(String typ)`: Alle Sitzplätze mit dem gleichen Typ sollen als `Sitzplatz[]` zurückgegeben werden. Das zurückgegebene Array darf jedoch keine `null`-Werte enthalten. 
	 **Hinweis:** Erzeugen Sie zuerst ein `Sitzplatz[]` der Größe `sitzplaetze.length * sitzplaetze[0].length`. Durchsuchen Sie danach alle Sitzplätze. Hat ein Sitzplatz den gesuchten Typ, speichern Sie den Sitzplatz in dem von Ihnen erzeugten Array ab. Nachdem Sie alle gesuchten Sitzplätze gespeichert haben, erzeugen Sie ein neues `Sitzplatz[]`, wobei die Größe des Arrays der Anzahl der gefundenen Sitzplätze entspricht. Verwenden Sie nun die Methode `System.arraycopy`, um die gespeicherten Sitzplätze in das neue Array zu bekommen. 
	- `sucheSitzplatzNr(String sitzplatzNr)`: Durchsucht den Rau, nach allen Sitzplätzen mit der angegebenen `sitzplatzNr`. Returnt den Sitzplatz, falls er gefunden wurde. 
	- `addSitzplatz(Sitzplatz s)`: Speichert den Sitzplatz `s` an der ersten freien Stelle im Raum. Wurde ein freier Platz gefunden, wird auch die `sitzplatzNr` gesetzt. Diese setzt sich zusammen aus dem ersten Zeichen der `raumNr` und aus dem Spalten- und Reihenwert, wo der Sitzplatz im Raum ist. Ist der Raum voll, wird der Sitzplatz nicht hinzugefügt. Beispiel für die `sitzplatzNr`: `A01` entspricht dem ersten Zeichen der `raumNr` (zB `A`), die erste Zahl für die Reihe (hier `0`) und die Zahl für die Spalte (hier `1`). 
	- `entferneSitzplatz(String sitzplatzNr)`: Entfernt den Sitzplatz mit der gegebenen `sitzplatzNr`aus dem Raum. Es soll der entfernte Sitzplatz zurückgegeben werden. 
	- `toString()`: Überschreiben Sie die `toString()`-Methode. Geben Sie einen String zurück, welcher alle Eigenschaften beinhaltet. 
	**Hinweis: ** Wenn Sie sich die `toString()`-Methode generieren lassen, wird normalerweise automatisch das Array ausgegeben. Manchmal passiert es jedoch, dass trotzdem nur die Speicheradressen angezeigt werden. Verwenden Sie in diesem Fall `Arrays.deepToString(arrayName)`.

**Beschreibung der `Gebäude`-Klasse:**
- Eigenschaften: 
	- Der Konstruktor soll `raeume` mit 3 Zeilen und 5 Spalten erzeugen. 
- Methoden: 
	- `addRaum(int geschoss, int stellplatz, String raumNr)`: Erzeugt einen neuen Raum mit der angegebenen `raumNr` und fügt es dem Gebäude an der richtigen Stelle hinzu. Befindet sich an dieser Stelle schon ein Raum, kann der neue Raum nicht hinzugefügt werden. 
	- `addSitzplatz(Sitzplatz s, int geschoss, int stellplatz)`: Fügt den angegebenen Sitzplatz an der angegebenen Stelle ein. 
	- `moveRaum(int geschoss, int stellplatz, int zielGeschoss, int zielStellplatz)`: Verschiebt den Raum von der Stelle `[geschoss, stellplatz]` an die Stelle `[zielGeschoss, zielStellplatz]`. 
	- `sucheSitzplatzNr(String sitzplatzNr)`: Sucht anhand der angegebenen `sitzplatzNr` nach einem Sitzplatz und gibt diesen zurück, falls er gefunden wurde. 
	- `sucheTyp(String typ)`: Alle Sitzplätze mit dem gleichen Typ sollen als `Sitzplatz[]` zurückgegeben werden. Das zurückgegebene Array darf jedoch keine `null`-Werte enthalten. 
	**Hinweis:** Erzeugen Sie zuerst ein `Sitzplatz[][]` der Größe `anzahlRaeume`, die zweite Klammer lassen Sie leer (damit haben wir eine variable Größe). Durchsuchen Sie danach alle Räume und verwenden Sie die `sucheTyp(String typ)`-Methode aus der `Raum`-Klasse. Hat ein `Raum` einen `Sitzplatz` mit dem gesuchten Typ, speichern Sie das resultierende Array des Aufrufs in dem von Ihnen erzeugten Array ab. Erzeugen Sie danach ein neues `Sitzplatz[]`, wobei die Größe des Arrays der Anzahl der gefundenen Sitzplätze entspricht. Schreiben Sie nun alle gefundenen Sitzplätze in das neue Array und geben Sie dieses zurück. 
	- `toString()`: Überschreiben Sie die `toString()`-Methode. Geben Sie einen String zurück, welcher alle Eigenschaften beinhaltet. 
	**Hinweis:** Wenn Sie sich die `toString()`-Methode generieren lassen, wird normalerweise automatisch das Array ausgegeben. Manchmal passiert es jedoch, dass trotzdem nur die Speicheradressen angezeigt werden. Verwenden Sie in diesem Fall `Arrays.deepToString(arrayName)`.

Um Ihr Programm zu testen, erstellen Sie eine `Main`-Klasse, welche die `main`-Methode beinhaltet:
- `main(String[] args)`: Testen Sie Ihr Programm, indem Sie die Methoden aufrufen. 

