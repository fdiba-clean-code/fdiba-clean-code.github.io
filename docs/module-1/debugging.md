# Was ist Debugging?
Debugging beschreibt die Tätigkeit ein Computerprogramm von einem technischen- oder inhaltlichen Fehler zu befreien.
Während das Debuggen selbst eigentlich keinen direkten Bezug zu Clean Code hat, so beeinflussen sich beide doch massiv.

Je "sauberer" der Code ist, desto eher besteht die Chance dass wir einen Bug noch während der Entwicklung entdecken. Zudem trägt gut strukturierter Code ungemein dazu bei, dass wir im Falle eines Problems in der Lage sind schnell die Ursache des Problems zu identifizieren und eine Lösung zu implementieren.

Hierbei können uns mehrere Dinge von Nutzen sein:

# Logging
Logging beschreibt die Ausgabe von zusätzlichen Informationen die nicht für den Endnutzer bestimmt sind. Log-Statements werden hierbei in der Regel in die Console ausgegeben oder zur späteren Analyse an ein externes System gesendet wie beispielsweise eine Datei auf der Festplatte oder ein zentrales Logging-Tool in der Cloud.

Hierbei sind folgende Punkte wichtig:

* 
Log Statements sollten hierbei die Informationen beinhalten, die später zur Lösung von Problemen tatsächlich nützlich sind. 

    * "Ein Fehler ist aufgetreten!" hilft niemandem. 

    * "Zeile 50 der Buchungs-Datei bookings-2022.csv konnte nicht vollständig gelesen werden" gibt einem Entwickler aber einen guten ersten Ansatz für die Fehlersuche.

* 
Die Menge an geschriebenen Log-Statements sollte über sogenannte "Log Levels" anpassbar sein - denn während wir während der Entwicklung oft möglichst viel Informationen auch von absolut erfolgreichen Events sehen wollen, so ist dies im produktiven Betrieb oft zu verwirrend. Hier wollen wir womöglich nur über kritische Fehler informiert werden.
* 
Logs dürfen auf keinen Fall persönliche oder sicherheitskritische Informationen beinhalten - dies gilt vor allem für Dinge wie Kreditkarten-Nummern etc.
# Debugger Tools
Debugger Tools sind Dinge mit denen ein Entwickler in der Lage ist eine Applikation während ihrer Ausführung zu pausieren und den internen Zustand der Applikation auszuwerten oder sogar zu verändern.
Der Punkt an dem die Applikation pausieren soll wird in der Regel über sogenannte "Breakpoints" im Code definiert.

Definiere ich beispielsweise einen Breakpoint innerhalb meiner doSomething() Funktion, so wird meine Applikation bei Erreichen von genau dieser Codezeile stoppen und ich kann damit beginnen die Werte von Variablen zu betrachten oder zu verändern.

Je nach Programmiersprache und -Umgebung kommen als Debugger-Tools verschiedene Applikationen zum Einsatz.
Für Java-Applikationen beispielsweise ist es in der Regel die IDE wie IntelliJ oder Eclipse welche die Debugger-Tools zur Verfügung stellt, wodurch ein Entwickler seine gewohnte Umgebung gar nicht erst verlassen muss.

Für web-basierte Applikationen auf Basis von JavaScript, welche in der Regel im Browser ausgeführt werden, bieten alle modernen Browser wie Chrome, Firefox und Safari ihre eigenen Entwickler-Tools mit Debugging Funktionalitäten.

## Eclipse Debugger View
![Eclipse Debugger](/img/debug.png)