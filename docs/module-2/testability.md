# Testbarkeit

Eine wichtige Eigenschaft von "Clean Code" ist, dass dieser testbar ist.
Ein Code ist dann gut testbar wenn mit relativ geringem Aufwand Unit- und andere Formen von automatisierten Tests geschrieben werden können. Diese Tests widerum sollen verlässliche Aussagen darüber treffen können ob ein Code jetzt und in der Zukunft immer noch korrekt arbeitet und sein Verhalten nicht gravierend verändert hat.

Mit Hilfe solcher automatisierten Tests sollen vor allem sogenannte Regressions-Fehler gefunden werden. Regressions-Fehler sind Fehler die entstehen wenn eine Änderung an einer Stelle im Code ungewollte&unerwartete Fehler an einer anderen Stelle hervorruft.

Die folgenden Kriterien haben Auswirkungen auf die Testbarkeit eines Code-Moduls:

## Code-Aufteilung entsprechend seines Zwecks
Um eine höhere [Cohesion](module-2/single-responsibility-principle) innerhalb des eigenen Codes zu erreichen ist es oft sinnvoll diesen entlang von Aufgabenbereichen zu trennen und aufzuteilen.
Besonders sinnvoll ist dies beispielsweise bei der Trennung zwischen Code zur Steuerung der grafischen Oberfläche und Code zur Ausführung von Geschäftsprozessen oder anderen Arten von Berechnungen.

Ist der Code entsprechend getrennt, so ist es deutlich einfacher automatiserte Tests (mindestens für Teile der Applikation) zu schreiben, da die einzelnen Module automatisch jeweils weniger Funktionalitäten und Verantwortlichkeiten haben.

## Dependency Inversion
Das Prinzip der Dependency Inversion ist eine Strategie um eine "loose Coupling" von Modulen im Code zu erreichen.

Ausgangslage ist hierbei meistens eine harte Abhängigkeit von 2 Klassen, bei denen mindestes eine Klasse ohne die andere nicht funktionieren kann und daher auch nicht unabhängig getestet werden kann:
![before-dependency-inversion.svg](/img/before-dependency-inversion.svg)

Wendet man nun das Konzept der Dependency Inversion an, so wird es notwendig eine zusätzliche Abstraktios-Ebene einzuführen, meistens in Form eines Interface oder Abstrakter Klasse. Während die eine Klasse nun das Interface implementiert und dementsprechend über die Methoden des Interface aufgerufen werden kann, so "kennt" die aufrufende Klasse nun ebenfalls nur noch das Interface und ruft die Methoden von diesem auf. Welche konkrete Implementation sich dahinter verbirgt ist nicht mehr bekannt oder relevant.
![after-dependency-inversion.svg](/img/after-dependency-inversion.svg)

Durch die zusätzliche Abstraktions-Ebene können nun in einem Unit Test sehr einfach "Test-Implementationen" unseres Interfaces erstellt und für die Tests genutzt werden.

## Pure Functions
Eine Funktion oder ein Modul ist dann "pure", wenn sie/er bei gleichen Parametern immer die gleichen Ergebnisse liefert und keine Auswirkungen oder Abhängigkeiten auf "externe" Module hat.

### Beispiel einer pure Function
Diese Funktion ist pure, da sie keinerlei Kontakt "nach außen" hat mit Ausnahme von den 2 Parametern.
Diese Funktion ist somit sehr einfach testbar, da wir keine komplexen Voraussetzungen erfüllen müssen um sie auszuführen.

```
public int sum(int numberA, int numberB) {
    return numberA + numberB;
}
```

### Beispiel von non-pure Funktionen
Diese beiden Funktion sind nicht "pure", da sie sie neben ihrer Parameter auch noch externe Aufrufe bzw Veränderungen durchführt.


```
// Um diese Funktion richtig zu testen brauchen wir eine reale oder simulierte "Datenbank", 
// welche uns den gewünschten Wert zurückliefert
public String generateMessageOfTheDay(String name) {
    String prefix = "Hello " + name + " this is your message of the day! \n";
    String messageOfTheDay = database.getMessageOfTheDayTemplate();
    
    return prefix + messageOfTheDay;
}
```

```
// Um diese Funktion richtig zu testen brauchen wir eine reale oder simulierte "Datenbank", 
// welche wir nach Ausführung überprüfen können ob das neue Datum gesetzt wurde.
public void updateDatabase() {
    Date now = new Date();
    database.setTimestampOfLastUpdate( now );
}
```

Für einen besser testbaren Code ist es oft sinnvoll seine Funktionen oder Module in pure und unpure Teile aufzuteilen - hierdurch wird zumindest ein Teil der Applikation sehr einfach testbar.
Um etwa das Message-Of-The-Day-Beispiel aufzuteilen könnten die Funktionalität in 2 Funktionen aufgeteilt werden:

``` 
// Wir haben die non-pure Funktionalitäten in diese Funktion verlagert
public void printMessageOfTheDay() {
    String name = "Skippy the Magnificent";
    String messageOfTheDayTemplate = database.getMessageOfTheDayTemplate();

    String messageOfTheday = generateMessageOfTheDay(messageOfTheDayTemplate, name);

    System.out.println(messageOfTheDay);
}

// Diese Funktion ist pure
public String generateMessageOfTheDay(String messageOfTheDayTemplate, String name) {
    String prefix = "Hello " + name + " this is your message of the day: ";
    return prefix + messageOfTheDayTemplate;
}


@Test
public void testMessageOfThDayGenerator() {
    String name = "Filthy Monkey";
    String messageOfTheDay = "Test 123";

    String expected = "Hello Filthy Monkey this is your message of the day: Test 123";

    String actual = generateMessageOfTheDay(messageOfTheDay, name);

    AssertEquals(expected, actual);
}

```