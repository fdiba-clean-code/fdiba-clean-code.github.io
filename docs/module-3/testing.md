# Automatisiertes Testen
Wie bereits in vergangenen Modulen gelernt, ist eines der wichtigsten Ziele des Clean Code, dass wir jederzeit sicherstellen können, dass unser Code **korrekt** ist. Code gilt hierbei dann als korrekt, wenn er das tut was ursprünglich für jede Funktionalität spezifiziert worden ist.


## Warum dies mit der Zeit immer schwieriger wird
Während es am Anfang einer Applikation oft noch relativ einfach ist zu prüfen, ob ein Code korrekt funktioniert, so wird dies mit steigener Komplexität und Größe einer Applikation immer und immer schwieriger. Dies liegt vor allem daran, dass die Beziehungen zwischen den Code-Modulen immer komplexer und unübersichtlicher werden - so kann eine kleine Änderung in Modul A plötzlich große Probleme in Modul B verursachen.

In der Praxis führt man daher in regelmässigen Abständen sogenannte Regressions-Tests durch. Diese Regressions-Tests haben das Ziel sicherzustellen, dass "alte" Funktionalitäten immer noch so funktionieren wie sie sollen.

Dies kann mit steigener Komplexität der Applikation aber sehr aufwändig werden, da sehr viele Menschen hiermit über einen langen Zeitraum beschäftigt werden.

Zur Veranschaulichung: Ein deutsches Bahnunternehmen rechnete im Jahr 2015 für das Regressions-Testen **einer** Applikation mit Kosten von *160.000 EUR* und einer Dauer von mehreren Wochen. Diese Regressions-Tests wurden mehrmals pro Jahr durchgeführt - für hunderte Applikationen.

## Die Lösung
Um diesen Aufwand (und die Kosten) zu begrenzen werden in der Praxis Tests so weit wie möglich automatisiert - dies hat den Vorteil, dass Tests im besten Fall nur einmal entwickelt werden müssen und danach de facto ohne weitere Kosten und in sehr kurzer Zeit ihre Ergebnisse liefern. Hierdurch kann sehr viel schneller Feedback dafür eingeholt werden, ob eine Applikation noch *korrekt* funktioniert.

Hierbei kommen verschiedene Arten von Tests zum Einsatz, die sich alle in ihrer Perspektive auf die Applikation aber auch auf andere Arten und Weisen unterscheiden.

![test-pyramid.png](/img/test-pyramid.png)


### Unit Tests
Als Unit Tests bezeichnet man Tests die nur kleine Einheiten von Code auf einmal testen, meistens nur eine einzelne Funktion. Unit Tests werden ausschließlich von Entwicklern geschrieben und unterstützen hierbei sowohl beim Regression-Testing als auch während der Entwicklung selbst.
Da Unit Tests aber Funktionen in Isolation testen - und oft sehr viel gemocked (simuliert) wird um sie ausführen zu können - haben sie gewisse Limitationen.
Unit Tests können gute Aussagen darüber treffen ob eine Funktion selbst funktioniert, sie können aber kaum eine Aussage darüber treffen ob eine Funktion noch kompatibel zum restlichen System ist.

- ✅ Sehr einfach und schnell zu erstellen
- ✅ Können sehr schnell ausgeführt werden, geben also schnelles Feedback
- ✅ Tests geben sehr verlässliches Feedback
- ✅ Fehler die hier aufkommen können sehr einfach identifizier werden
- ❌ Unit Tests testen Funktionen nur auf kleinster Ebene
- ❌ Unit Tests können keine Aussage darüber treffen ob Module zusammen funktionieren


### Integration Tests
Integration Tests gehen einen Schritt weiter als Unit Tests. Mit Hilfe von Integration Tests prüfen wir ob unsere Code-Module nicht nur für sich alleine sondern auch gemeinsam funkionieren.
Beim Integration Testing werden hierbei also zwei oder mehr Module gestartet, welche dann gemeinsam automatisiert einen Testfall ausführen.
Integration Tests sind hierbei ein Zwischenschritt zwischen Unit Tests und E2E Tests, weil sie zwar komplexere Prozesse testen, dies aber nicht auf die Art tun wie es ein Mensch in der Regel tun würde. Integration Tests interagieren also in der Regel nicht mit einer grafischen Oberfläche etc. (wobei es hier Ausnahmen gibt).

- ✅ Kann komplexe Szenarien testen
- ✅ Gibt relativ präzises Feedback über die Fehler-Ursache
- ❌ Aufwändig/teuer zu supporten
- ❌ Erstellung von Tests kann unter Umständen aufwändig sein
- ❌ Manchmal zeitaufwändig in der Ausführung

### E2E Tests
End-to-End Tests (E2E) sind automatisierte Tests die eine Applikation fast wie ein Mensch bedienen. Technisch basieren sie meistens auf Automatisierungs-Werkzeugen die einen (fast) normalen Browser oder ähnliches benutzen um ganz normale Mausklicks, Tastatureingaben etc. durchzuführen.
Hierbei wird unsere Applikation so installiert und benutzt, wie sie auch im realen Leben benutzt werden würde.
E2E Tests werden in manchen Unternehmen von den Entwicklern selbst geschrieben, in anderen Unternehmen aber

- ✅ Kann komplexe Szenarien testen, von Anfang bis Ende
- ✅ Bedient die Applikation wie ein echter Mensch
- ❌ Sehr aufwändig/teuer zu supporten
- ❌ Tests werden über die Zeit "flaky" (sogar kleine Änderung in z.B. einem Text können zu Problemen führen)
- ❌ Sehr zeitaufwändig in der Ausführung (oft mehrere Stunden), geben also kein direktes Feedback
- ❌ Die Ursache für Probleme die hier auftreten können oft nur sehr schwierig gefunden werden


### Wie und wieviel sollte man testen?
Wie viel und was genau getestet werden sollte - und auf welche Art und Weise man dies testet - ist in jeder Organisation und für jede Applikation eine schwierige Frage.
Jede Applikation hat ihre eigenen Anforderungen an die Menge an Fehlern die noch akzeptabel sind: Während ein kleiner Bug auf einer Hotel-Website wahrscheinlich kein großes Problem ist, sieht dies für die Steuerungs-Software für einen medizinischen Roboter ganz anders aus.

Absolute Aussagen wie "Unit Tests für mindestens 80% des Codes" sind daher in der Praxis zwar oft verbreitet aber meistens eher ungeeignet. Für jede Applikation sollt konkret entschieden werden was genau getestet werden soll und welche Techniken hierfür zum Einsatz kommen sollten.