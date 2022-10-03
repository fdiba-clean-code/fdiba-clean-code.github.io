# Das Problem mit den Kommentaren im Code...
Kommentare im Code werden von verschiedenen Personen und Organisatione sehr unterschiedlich betrachtet und es gibt keine wirklich 100% einheitliche Lösung wie man mit Kommentaren im Code umgehen soll.

Viele Organisationen erwarten von ihren Entwicklern, dass der gesamte Code kommentiert ist und die Kommentare selbst die Funktionalität als auch die Beziehungen des Codes selbst klar beschreiben. Dies ist vor allem in Organisationen der Fall in denen Richtlinien vorrangig von Personen etabliert werden, die selbst nur wenig Erfahrung mit dem Schreiben von Software haben.

Dem gegenüber stehen die Puristen, welche die Meinung vertreten Kommentare sind im besten Fall nutzlos, im schlimmsten Fall sogar störend und verschlechtern die Verständlichkeit von Code.

# Kommentare aus der Sicht des Clean Code

Aus der Perspektive des "Clean Code" sollten Kommentare möglichst selten genutzt werden. 
Kommentare sollten vor allem dann eingesetzt werden, wenn im Code etwas passiert was nicht durch den Code selbst erklärt werden kann - dies bezieht sich also vor allem auf die Fragen wie "WARUM tut der Code das, was er hier tut?"

Kommentare die den Zweck haben zu erklären WAS der Code selbst tut sind in fast allen Fällen eher ein Zeichen dafür, dass der Code selbst zu kompliziert ist und überarbeitet werden sollte. Mit besseren Namen und Vereinfachung des Codes selbst, können fast alle solcher Kommentare überflüssig gemacht werden.

In Ausnahmefällen können Kommentare nützlich sein um Code zu erklären, der sehr schwierig zu verstehen ist aber leider nicht weiter vereinfacht werden kann. Dies ist oft der Fall bei Dinge die Regulären Ausdrücken (RegEx)

# Die Gefahr der Kommentar

Jeder Kommentar der geschrieben wird, muss stets geupdated werden wenn sich die Funktion auf die er sich bezieht ändert. Dies ist nur ein kleines Problem bei wenigen Kommentaren die sich vorrangig um das "WARUM" kümmern - kann jedoch zu einem sehr großen Problem werden wenn diese Regel nicht eingehalten wird.
Jeder Entwickler kommt in seiner Karriere einmal an den Punkt dass er auf ein Problem stösst dass er partout nicht lösen kann, trotz viel Zeit und Arbeit - nur um dann Tage später zu bemerken dass die Kommentare die den Code beschrieben haben den er nutzt, nicht mehr mit der eigentlichen Implementation übereinstimmen. Irgendwann wurde vergessen bei einer Änderung die Kommentare mit zu aktualisieren.

## Beispiele für gute Kommentare
```
// Matches a Dutch zipcode, eg, '1974 XA' or '4844RA'
Pattern DUTCH_ZIPCODE = Pattern.compile("[1-9][0-9]{3} ?[A-Z]{2}");
```

```
int resultCode = ...;
boolean isSucess = resultCode == 200;
boolean isTemporaryError = resultCode == 503 || resultCode == 504;
// Sometime we receive a temporary error. 
// However, in all cases which were researched, results were successfully stored.
// Because of this we will return true in that case.
return (isSucess || isTemporaryError);
```

# Anti-Patterns

## Danke, Captain Obvious
```
// numeric session-id
int sessionId = 0;
 
// expiry date
Date expiry = new Date();

// numeric session-id
int sessionTimeoutInSeconds = 3600;

// resets session-id to 99;
function reset() {
    sessionId = 99;
}
```

## Erklärt unklaren Code
```
// timeout in seconds
int timeout = 5; // <---- nicht gut

int timeoutInSeconds = 5; // <---- besser



// if during work hours
if (currentTime.hours >= 9 && currentTime.hours <= 17) // <---- nicht gut


if (isDuringWorkingHours(currentTime)) // <---- besser
```

## Auskommentierter Code
Entwickler neigen vor allem am Anfang ihrer Karriere dazu Code auszukommentieren aus Angst ihn zu verlieren und dann später noch eimal zu brauchen.
Dieses "Feature" ist gut gemeint, führt aber vor allem zu aufgeblähtem und schwer lesbaren Code - und wird so gut wie nie wirklich gebraucht. Zudem ist das Ziel selbst schon vom Source Control System erfüllt, denn hier kann auch gelöschter Code notfalls wieder hergestellt werden.


# Quellen
* [https://www.baeldung.com/cs/clean-code-comments](https://www.baeldung.com/cs/clean-code-comments)
* [https://medium.com/codex/clean-code-comments-833e11a706dc](https://medium.com/codex/clean-code-comments-833e11a706dc)