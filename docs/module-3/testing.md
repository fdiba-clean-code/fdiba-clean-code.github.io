# Automatisiertes Testen
Wie bereits in vergangenen Modulen gelernt, ist eines der wichtigsten Ziele des Clean Code, dass wir jederzeit sicherstellen können, dass unser Code **korrekt** ist. Code gilt hierbei dann als korrekt, wenn er das tut was ursprünglich für jede Funktionalität spezifiziert worden ist.

## Warum dies mit der Zeit immer schwieriger wird
Während es am Anfang einer Applikation oft noch relativ einfach ist zu prüfen, ob ein Code korrekt funktioniert, so wird dies mit steigener Komplexität und Größe einer Applikation immer und immer schwieriger. Dies liegt vor allem daran, dass die Beziehungen zwischen den Code-Modulen immer komplexer und unübersichtlicher werden - so kann eine kleine Änderung in Modul A plötzlich große Probleme in Modul B verursachen.

In der Praxis führt man daher in regelmässigen Abständen sogenannte Regressions-Tests durch. Diese Regressions-Tests haben das Ziel sicherzustellen, dass "alte" Funktionalitäten immer noch so funktionieren wie sie sollen.

Dies kann mit steigener Komplexität der Applikation aber sehr aufwändig werden, da sehr viele Menschen hiermit über einen langen Zeitraum beschäftigt werden.

Zur Veranschaulichung: Ein deutsches Bahnunternehmen rechnete im Jahr 2015 für das Regressions-Testen **einer** Applikation mit Kosten von *160.000 EUR* und einer Dauer von mehreren Wochen. Diese Regressions-Tests wurden mehrmals pro Jahr durchgeführt - für hunderte Applikationen.

## Die Lösung
Um diesen Aufwand (und die Kosten) zu begrenzen werden in der Praxis Tests so weit wie möglich automatisiert - dies hat den Vorteil, dass Tests im besten Fall nur einmal entwickelt werden müssen und danach de facto ohne weitere Kosten und in sehr kurzer Zeit ihre Ergebnisse liefern. Hierdurch kann sehr viel schneller Feedback dafür eingeholt werden, ob eine Applikation noch *korrekt* funktioniert.

Hierbei kommen verschiedene Arten von Tests zum Einsatz

![test-pyramid.png](/img/test-pyramid.png)