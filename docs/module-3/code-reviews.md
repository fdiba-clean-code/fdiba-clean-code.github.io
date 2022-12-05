# Code Reviews

Code Reviews, welche auch als Peer Reviews bekannt sind, beschreiben die Tätigkeit, dass ein Entwickler seine Code-Änderung von einem (oder mehreren) anderen Entwicklern prüfen lässt. Diese Prüfung hat das Ziel, dass mögliche Fehler oder unsauberer Code schon identifiziert und beseitigt werden können bevor ein neuer Code der "Allgemeinheit" zur Verfügung gestellt wird.

# Praktische Anwendung

In der Regel geschehen Code Reviews in modernen Organisationen auf Basis von Merge Requests. Beim Mergen von einem Feature-Branch in den Haupt-Branch unterstützen moderne Tools wie Github oder Azure DevOps dabei, alle Änderungen die zu einem Merge Request gehören leicht identifizierbar zu machen.
In der Regel werden hierbei die Änderungen farblich hervorgehoben und neben dem ursprünglichen Code dargestellt, wodurch ein "Vorher/Nachher" Vergleich einfach möglich wird.

Ist ein Merge Request erstellt so können ein oder mehrere andere Entwickler diesen Merge Request ansehen und zu einzelnen Code-Zeilen oder -Passagen Kommentare hinterlassen.
Diese Kommentare können Bezug nehmen auf viele verschiedene Dinge:

- Mögliche Bugs
- Nicht beachtete Anforderungen
- Fehlgeschlagene/Fehlende Tests
- Unsauberer Code
- und viele weitere Dinge

Nachdem der Entwickler eines Merge Requests sein entsprechendes Feedback erhalten hat, so liegt es an ihm seinen Code entsprechend zu korrigieren und eine weitere Iteration im Code-Review Prozess zu starten. Dieser Zyklus wird so oft wiederholt bis die geforderte Zahl von "Approvals" erreicht worden ist. Die Menge der benötigten Approvals ist von Organisation zu Organisation unterschiedlich und kann 1 oder mehrere ausmachen.

# Wichtige Kriterien beim Code Review

Beim Code Review gibt es sowohl für den Reviewer als auch den Reviewee einige wichtige Dinge zu beachten.
Wichtig für beide gemeinsam ist es, den Zyklus zwischen Feedback und Korrekturen sehr schnell zu halten. Code Reviews sowieso Korrekturen sollten daher so schnell wie möglich ausgeführt werden, um für alle Beteiligten das Wissen noch frisch im Gedächtnis zu halten.

Für den Reviewer ist es zudem wichtig, klares Feedback zu geben um die Erwartungshaltung dem Reviewee gegenüber leicht verständlich zu machen. Da oft ein unterschiedlicher Erfahrungsstand zwischen den einzelnen Entwicklern existiert, ist es oft wichtig bei einem Code Review auch einige Hintergründe zu erklären WARUM ein bestimmtes Review oder Korrektur-Vorschlag abgegeben wurde.

# Github Merge Request Screenshot

![Github Screenshot](/img/github-mr.png)
