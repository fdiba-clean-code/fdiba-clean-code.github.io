# Statische Codeanalyse

Statische Codeanalyse ist ein Testverfahren, bei dem der Code noch vor der Ausführung auf bestimmte Fehler untersucht wird. Statische Codeanalysen lassen sich gut in einen CI/CD-Workflow einbauen, damit sie beispielsweise bei jedem merge durchgeführt werden. Beliebte Tools für diesen Zweck sind unter anderem SonarQube oder SonarCloud.

Ein Report in SonarCloud für das Spiel Fdibamon sieht zum Beispiel so aus:

![image](https://user-images.githubusercontent.com/113884419/205060086-73be3329-0ca3-4b21-87f7-530035502ec7.png)

Sonar unterscheidet unter anderem zwischen Bugs, Vulnerabilities und Code Smells. Bugs sind Fehler, welche bei der Ausführung zu falschen Ergebnissen oder unerwünschtem Verhalten führen können, Vulnerabilities sind Sicherheitslücken und Code Smells sind Probleme, die zwar keine Fehler erzeugen aber den Code schwieriger lesbar oder maintainable machen (zum Beispiel unbenutzte Imports oder unnötig verschachtelte If-statements).
