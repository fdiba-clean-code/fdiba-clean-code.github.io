# Refactoring
In vorherigen Kapiteln haben wir diverse Strategien betrachtet wie wir beim Schreiben von Code eine gute Qualität erreicht können. Was aber wenn wir oder ein anderer Entwickler bereits suboptimalen Code geschrieben und in unsere Applikation integriert haben? 

Es gibt vorrangig 2 Gründe warum wir über die Zeit existierenden Code verändern oder verbessern müssen:

1. Es haben sich Anforderungen oder Rahmenbedingungen geändert
2. Existierender Code erfüllt nicht unsere Qualtätsanforderungen

Das Ändern unseres Codes ohne Veränderung der eigentlichen Funktionalität nennt man **Refactoring** - und es hat grundsätzlich immer zum Ziel eine dieser beiden problematischen Situationen zu verbessern.

## High Coupling
Wir als Entwickler stehen oft vor dem Dilemma, dass der Code den wir refactoren wollen so tief in unsere restliche Applikation verworren ist, dass er nur sehr schwierig verändert oder erweitert werden kann. Möglicherweise etwa gibt es sehr viele andere Module die konkret gegen diese eine Implementation unseres Code entwickelt haben, wodurch jede Änderung plötzlich ungewollte Seiteneffekte mit sich bringt.
Diese Situation ist "High Coupling", de facto das Gegenteil dessen was wir in "clean code" eigentlich erreichen wollen.

## Refactoring by Abstraction
Während das Refactoring bei vergleichsweise kleinen Modulen und Applikationen noch relativ einfach ausgeführt werden kann, so kann dies bei sehr großen und komplexen Applikationen eine große Hürde darstellen.
Eine Strategie die sich zur Lösung dieses Problems bewährt hat ist das Refactoring by Abstraction. Ähnlich wie beim Dependency Inversion gehes auch hier darum eine weitere Abstraktionsebene zwischen 2 Code-Modulen einzuführen.

Mit Hilfe dieser Abstraktions-Ebene können auf beiden Seiten der Abstraktion nach und nach kleinere oder größere Änderungen vorgenommen werden, ohne dass dies negative Auswirkungen auf die jeweils andere Seite haben muss.

![refactor-by-abstraction.png](/img/refactor-by-abstraction.png)

