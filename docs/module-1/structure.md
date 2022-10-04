# Wie sieht guter Code aus?

## Der Code ist nicht zu groß
Funktionen und Klassen sollten möglichst klein gehalten werden, damit sie einfacher zu lesen sind und damit sie nicht zu viel auf einmal tun.

## Der Code folgt den Konventionen
Jede Programmiersprache und/oder jede Organisation folgt in der Regel einer Konvention wie Code strukturiert und aufgebaut sein sollte. Code der diesen Konventionen folgt ist einfacher zu lesen und schneller zu verstehen von Entwicklern die diese Konvention schon gewöhnt sind.
Zudem sind in den Konventionen oft "Tricks" versteckt, welche unter bestimmten Umständen Fehler verhindern können.

Google beispielsweise veröffentlicht sehr gute Styleguides:

* [Google Java Styleguide](https://google.github.io/styleguide/javaguide.html)
* [Google Python Styleguide](https://google.github.io/styleguide/pyguide.html)

## Der Code Enthält keine/kaum Duplikate
Duplikate / der gleiche Code mehrfach in der Applikation führt oft zu Problemen, da sich der Entwickler immer daran erinnern muss dass er eine Änderung an einer Stelle auch an allen anderen Stellen nachholen muss. Dies wird bei wachsender Code-Größe zu einem immer schwierigeren Problem

## Der Code beinhaltet Whitespaces für die Lesbarkeit
Dicht aneinander geschriebener Code ohne jegliche Leerzeilen etc. ist für Menschen sehr schwer zu lesen. Gelegentliche Leerzeilen und Leerzeichen helfen. Der Code ist hierbei stehts konsistent!

## Der Code ist richtig eingerückt
Richtiges Einrücken vom Code steigert die Lesbarkeit ungemein - und während es in Programmiersprachen wie Java "nur" der Lesbarkeit dient, wirkt sich das Einrücken vom Code in Sprachen wie Python sogar auf die gesamte Funktionalität aus!

## Der Code beinhaltet keine Magic Numbers
Magic Numbers beschreiben Zahlen oder Werte im Code, die für einen Leser nicht direkt offensichtlich sind. Magic Numbers sollten mit der Hilfe von Konstanten oder ähnlichen Konstrukten weiter erklärt werden
```
if(age >= 20) {
    executeCode();
}
```
Besser:
```
public static final int LEGAL_DRINKING_AGE_IN_JAPAN = 20;

(...)

if( age >= LEGAL_DRINKING_AGE_IN_JAPAN) {
    executeCode();
}
```

## Der Code kapselt komplexe Logik
Komplexe Logik (z.B. große IF Abfragen) können sehr schwierig zu lesen und zu verstehen sein, wodurch sie auch den Code um sie herum beeinflussen kann und schwieriger zu supporten macht.
Um dies etwas zu verbessern sollte komplexe Logik via "Zwischen-Variablen" oder am besten gleich in dedizierte Funktionen gekapselt werden.

Nicht gut:

```
if ( employee.age > 55 
    && employee.yearsEmplyed > 10
    && employee.isRetired ) {
    // do something 
}
```
Besser:

```
bool eligibleForPension = employee.age > minRetirementAge
                       && employee.yearEmployed > minPensionEmploymentYears
                       && emplyee.isRetired ; 
```
Noch besser: 
```
private boolean isEligbleForPension(Employee employee) {
    return employee.age > minRetirementAge
        && employee.yearEmployed > minPensionEmploymentYears
        && emplyee.isRetired;
} 

(...)

if( isEligbleForPension(employee) ) {
    // do something 
}
```