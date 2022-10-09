# Fehlerbehandlung

## Einleitung
Das Auftreten und Behandeln von Fehlern gehört zum Alltag jeder Applikation und zur täglichen Arbeit eines jeden Entwicklers.
Ob ein Fehler auftritt weil unser Code selbst diesen verursacht hat oder wir von einem externen System oder Modul abhängen und dieses widerum einen Fehlerzustand festgestellt hat ist hierbei nicht wichtig - wichtig ist nur, dass wir als Entwickler auf diesen Umstand reagieren müssen

## Unterscheidung der Arten von Fehlern

Beim Schreiben von Code zur Behandlung von Zuständen die einen Fehler darstellen ist es zuerst am wichtigsten zu identifizieren ob wir selbst mit unserem Code diesen Zustand behandeln/lösen können oder nicht.

Können wir den Fehler behandeln, lösen oder umgehen - so ist es im Zweifel nur eine weitere Funktion oder ein weiteres Modul welches wir entwickeln müssen um das Problem zu lösen und einen "normalen" Zustand wieder herzustellen.

Können wir mit unserem Code den Fehler jedoch nicht lösen (etwa, weil er ein Feedback vom Nutzer braucht, unser Code aber ein Java-Backend-System ohne direkten Zugriff zum User ist), so müssen wir auf sogenannte Exceptions zurückgreifen.

## Was sind Exceptions
Exceptions sind als Paradigma in fast allen modernen Programmiersprachen vorhanden und beschreiben in der Regel gleichzeitig eine Veränderung des Kontrollflusses (also der Code der als nächstes ausgeführt wird) als auch ein Objekt mit Meta-Informationen zum aufgetretenen Fehler.
Exceptions haben sich in der Praxis als besseres Paradigma als "Return Codes" herausgestellt, welche vor allem in früheren Programmiersprachen- und umgebungen sehr verbreitet waren.
Return Codes haben den Nachteil, dass sie sehr viel Interpretation durch den Empfänger des Return Codes benötigen und meistens sehr wenige dazugehörige Meta Informationen zur Verfügung stellen, welche zur Lösung des Problems womöglich sinnvoll wären.

## Wie nutze ich Exceptions
Jede Programmiersprache hat zum Thema Exceptions ihren eigenen Syntax und Konzepte - wobei sich das Grundparadigma kaum unterscheidet.
Betrachtet werden können immer 2 Szenarien:

### Szenario 1 - Werfen von Exceptions
Erkennt unser Code einen Fehler den wir selbst nicht behandeln können, so wird das Werfen einer Exception sinnvoll.
Wir erstellen hierbei ein typisiertes Exception-Objekt welches wir mit Informationen füllen die dem "Empfänger" dieses Objekts ggf. nützlich sind um den Fehler behandeln zu können.
Es ist hierbei wichtig dass wir sinnvolle Informationen und Exception-Typen wählen, um dem Empfänger unserer Exception die beste Chance zu geben das Problem zu lösen oder zu behandeln.
``` 
if( somethingBadHappened) {
    throw new MyException("Dieser String");
}
``` 
Der Programmfluss wird hierbei beim Werfen der Exception unterbrochen, "unser" Code wird nicht weiter ausgeführt sondern die Exception wandert in der Funktions-Hierarchie weiter nach oben bis es einen korrespondierenden Handler/Catch-Block erreicht.
Gibt es in der gesamten Funktions-Hierarchie keinen passenden Exeption-Handler, so wird in der Regel die gesamte Applikation beendet.

### Szenario 2 - Fangen von Exceptions
Haben wir Code oder Funktionen aufgerufen die unter Umständen Exceptions werfen, so liegt es an uns diese Exceptions zu "fangen" **wenn wir sie behandeln können**. Ist unser Code aus irgendwelchen Gründen nicht in der Lage die Exception zu behandeln, so sollten wir sie gar nicht erst fangen um einem anderen Modul weiter "oben" in der Hierarchie die Möglichkeit zu geben diese Exception zu behandeln.

In der Java-Welt besteht ein Exception-Handling aus 3 Code-Blöcken die zueinander gehören.
* Try Block - dies ist der Code Block, in dem wir Exceptions erwarten und bei deren Auftreten wir reagieren wollen
* Catch-Block - in 0-n Catch-Blöcken "fangen" und behandeln wir möglicherweise auftretende Exceptions für jeweils 1 bestimmten Typ
* Finally-Block - dieser Block beschreibt Code der definitiv ausgeführt werden soll, egal ob eine Exception aufgetreten ist oder nicht

```
try {
    callMyFunction();
} catch (MyException e) {
    displayErrorToUser(e.getMessage());
    setErrorState(true);
} finally {
    System.out.println("The function has finished");
}

```

## Wie designe ich Exceptions
Die meisten Programmiersprachen beinhalten selbst schon eine eigene Hierarchie von Exception-Typen, welche ihrerseits diverse Fehlerszenarien beschreiben. Es ist sinnvoll diese zu nutzen und ggf. um eigene Typen zu erweitern, wobei sich hier oft die Vorteile der Abstraktion zeigen.

## Wie funktioniert es in Java?
Java unterscheidet grundsätzlich zwischen Exceptions und Errors, wobei beide Arten (und ihre Unterarten) das Interface "Throwable" implementieren.

Exceptions in der Java-Welt stellen Fehler und Zustände dar, von denen eigentlich zu erwarten ist dass eine Applikation diese auf irgendeine Weise behandelt und/oder weitergibt.
Errors auf der anderen Seite stellen Zustände dar über die die Applikation zwar informiert wird aber welche dann in der Regel nicht behandelt werden (können).
OutOfMemoryError oder StackOverflowError beispielsweise sind 2 Fehlertypen bei denen die Applikation nicht weiter reagieren kann - da ihr Auftreten zur Terminierung der Applikation führt.

## Wann sollte ich keine Exceptions nutzen?
Exceptions sollten vor allem in den Momenten nicht genutzt werden, wo die Applikation sich eigentlich noch in einem normalen Zustand und Fluss befindet. Dies hat vor allem zwei Gründe:
+ Das Nachverfolgen von einem durch Exceptions kontrollierten Programmfluss ist für einen Entwickler relaltiv schwierig
+ Exceptions sind aus Performanceperspektive relativ "teure" Operationen (mindestens in Java) und könnten in performancekritischen Code zu Verlusten führen.