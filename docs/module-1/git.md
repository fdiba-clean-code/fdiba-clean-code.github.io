# Was ist Source Control?

Source Control beschreibt die Versionierung von Source Code, also das Speichern aller Code-Dateien zu einem bestimmten Zeitpunkt. Das Source Control System hat hierbei die Aufgabe sicherzustellen, dass ein Nutzer auch später zu einer früheren Version seines Source Codes zurückkehren kann - etwa um zu Vergleichen was sich geändert hat oder um komplett auf eine frühere Version zurückzukehren.

# Was hat Source Control mit Clean Code zu tun?

Ohne Source Control ist es sehr schwierig Source Code über eine lange Zeit sauber und wartbar zu halten.
Entwickler verlieren die Übersicht darüber wann, von wem welche Änderung gemacht worden ist, was vor allem dann zu Problemen führt wenn mehrere Entwickler am gleichen Projekt arbeiten.
Beim Austausch von Code zwischen Entwicklern wird es sehr schwierig nachzuvollziehen welche Datei geändert worden ist und ob sich hieraus vielleicht Probleme ergeben, weil der neue Code von Entwickler A nicht zum neuen Code von Entwickler B passt.

Ein Source Control System hilft dabei einen Code sauber und kompatibel zu behalten - auch wenn es weiterhin an den Entwicklern liegt, dies alles sicherzustellen.

# Was ist Git?

Git ist das Source Control System das sich als de facto Standard in der gesamten IT Welt durchgesetzt hat. Es ist hierbei ein sogenanntes Distributed Source Control System, d.h. jeder Client (meistens Entwickler-Computer) hält die gesamte Historie und den gesamten Source Code des Projekts.
Jedes "Commit" vom Code und jeder "Push" zu einem anderen Client überträgt hierbei widerum die gesamten letzten Änderungen, nicht nur den finalen/aktuellen Stand.

# Commit, Push...?

Die folgenden Begriffe beschreiben die Haupt-Funktionalitäten von Git (sowieso eigentlich auch jedes anderen Source Control Systems).

Eine kurze offizielle Einführung zu Git findet ihr [hier](https://git-scm.com/book/en/v2/Git-Basics-Getting-a-Git-Repository)
Eine detailliertere Referenz zu Git befindet sich [hier](https://git-scm.com/docs)

## Repository

Ein Git Repository ist eine Menge an Dateien die in Git verwaltet werden. Ein Repository besteht hierbei aus den Dateien selbst, mehreren Branches (d.h. parallelen Versionen) sowie der Historie/den Änderungen über die Zeit.

## Clone

Das Clonen eines Projekts ist das erste "Downloaden" eines Git Repositories auf die lokale Workstation, in der Regel vom zentralen Repository.

## Pull

Ein Git Pull ist das "Downloaden" von allen Änderungen die im zentralen Repository seit dem letzten Git Pull passiert sind.

## Branch

Branches beschreiben parallele Bearbeitungs-Stände innerhalb eines Git Repositories.
Ein Beispiel hierbei wäre ein Projekt mit 2 Entwicklern. Jeder Entwickler arbeitet an unterschiedlichen Features - aber sie müssen beide gleichzeitig die gleichen Dateien verändern. Um also nicht ständig Probleme mit den Änderungen des jeweils anderen Enwicklers zu bekommen startet jeder der Entwickler einen sogenannten "Branch". Solange er auf diesem Branch arbeitet, kann er jederzeit alle Dateien ändern aber der jeweils andere Entwickler sieht keine dieser Änderungen.
Erst wenn sein Branch zurück in den Haupt-Branch "gemerged" wird, werden seine Änderungen für alle anderen sichtbar.

Beim Branching entstehen sehr oft "Merge Conflicts", d.h. Probleme die daraus entstehen dass die gleiche Dateien in verschiedenen Branches verändert worden sind. Um dies zu reparieren muss in der Regel ein Entwickler beide Code-Versionen vergleichen und diese Zusammenführen.
Je länger kein Merge stattgefunden hat, desto schwieriger wird das Mergen - es ist daher extrem wichtig so früh wie möglich einen Merge durchzuführen und einen Branch wieder zu löschen. Zudem sollten regelmässig die letzten Änderungen vom Haupt-Branch übernommen werden.

## Commit

Ein Commit ist das Abspeichern von einem Code-Stand zu einem bestimmten Zeitpunkt. Ein Commit beinhaltet normalerweise 1..n Dateien zusammen mit einer Commit Message, welche die Änderung beschreibt.
Es ist bei einem Commit wichtig mit allen Entwicklern eine gemeinsame Konvention zu etablieren, wie Commit-Messages verfasst werden sollen. In der Regel beinhalten Commit-Messages daher oft die ID des Work Items zu dem diese Änderung gehört zusammen mit einer kurzen Beschreibung der eigentlichen Änderung.

> git commit -m "bug/123 Fixed validation logic for german zip codes"

## Add/Stage

Beim "Adden" einer Datei nehmen wir sie in die Versionierung durch Git in diesem Repository mit auf. Bevor eine Datei geaddet wurde, werden ihre verschiedenen Versionsstände von Git ignoriert und nicht mit gespeichert.

Beim Stagen markieren wir eine Änderung an einer Datei so, dass wir sie beim nächsten Commit mit "committen" wollen. Wenn eine Änderung nicht "gestaged" wurde, dann wird sie in der Regel bei einem Commit ignoriert. Es können nur Änderung von bereits "geaddeten" Dateien gestaged werden.

## Push

Ein Push überträgt lokale Änderung (durch Commits) an ein anderes Git System, ein sogenanntes "Remote". Dies könnten theoretisch auch andere Entwickler Computer sein, in der Praxis hat sich aber etabliert dies an ein zentrales Repository zu senden, zu dem jeder Entwickler Zugriff hat. In den meisten Fällen wird dies ein System wie Github, Gitlab, Azure DevOps etc. sein.

> git push origin master

## .gitignore File

Das .gitignore File in einem Projekt beschreibt die Dateien, die nicht mit in das Repository commited werden sollen. Dies sind in der Regel vor allem Dateien die
immer wieder automatisch generiert werde (Builds)
Secrets enthalten (z.B. Passwörter, Secrets)

# Ein einfaches Beispiel

> git init  
> git add .  
> git commit -am "First commit"  
> git remote add origin git@github.com:your_github_user/myapplication.git  
> -- Change/write README.md and .gitignore files  
> git pull origin main  
> -- Send the entire application to Github  
> git push origin main
