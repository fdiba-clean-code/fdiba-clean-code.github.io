# Automatisierte Formatierung
Da die Formatierungsregeln die Code-Ökosysteme oder Organisationen oft sehr komplex und arbeitsaufwändig werden können, werden in der Praxis oft verschiedene Möglichkeiten zur Automatisierung und automatischer Kontrolle genutzt.

Hier folgen nun einige Möglichkeiten Formatierungsregeln automatisch anzuwenden und zu prüfen:

## Regelwerke in der Entwicklungsumgebung
Jede moderne Entwicklungsumgebung wie Visual Studio Code oder IntelliJ bringt eigene (konfigurierbare) Formatierungsregeln für verschiedene Programmiersprachen mit.
Diese Formatierungsregeln können entweder bei Verstoss als Warnung ausgegeben werden oder direkt beim Speichern einer Datei automatisch angewendet werden.
Diese in der Entwicklungsumgebung zu nutzen hat für einen Entwickler den Vorteil, dass sie sehr einfach und komfortabel zu benutzen ist - hat jedoch den Nachteil, dass verschiedene Entwicklungsumgebungen (die durchaus gleichzeitig im selben Team benutzt werden können) unterschiedliche Regeln haben können.
Diese müssen dann entweder aneinaner angepasst werden oder das Team muss mit einer gewissen Abweichung in der Formatierung leben.

## Formatter-Tools
Um unabhängiger von einzelnen Entwicklungsumgebungen zu sein gibt es auch "unabhägige" Tools wie z.B. "Prettier", welche entweder als IDE-Plugin oder via Kommandozeile aufgerufen werden können und dann ihrerseits automatische Code-Formatierungen anhang von komplexen Regeln anwenden können.

Diese Tools haben zudem zwei weitere Vorteile:

1. Sie sind "opinionated", d.h. sie bringen von Haus aus fixe Regeln mit sich die sich aus Best Practices heraus ergeben haben
2. Sie können via Git Hooks oÄ automatisch angewendet werden wodurch sie forciert angewendet werden bevor der Sourcecode das Git Repository erreicht

## Git Hooks
Git Hooks sind Trigger die bei bestimmten Aktionen im Git automatisch ausgeführt werden.
Ein verbreitetes Beispiel hierfür sind "Git Pre-Commit"-Hooks. Hierbei werden in dem Moment wo ein User ein Git Commit ausführt automatisch weiterer Code ausgeführt - wie beispielsweise das Code Formatting Tool "Prettier"