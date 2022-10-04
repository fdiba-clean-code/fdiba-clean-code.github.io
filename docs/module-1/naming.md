# Warum Namen wichtig sind
Das Auswählen von Namen für Funktionen, Klassen und Variablen wirkt auf den ersten Blick unwichtig, ist in der Praxis jedoch eines der wichtigsten Momente im Entwicklungsprozess.

# He who shall be named
Indem wir Funktionen, Klassen und Variablen ihre Namen geben, erreichen wir zwei wichtige Dinge:

* Wir definieren ihre Aufgabe und wir begrenzen ihren Scope
* Wir geben dem Leser vom Code Informationen über das was er gerade liest

Beim Vergeben von Namen müssen wir also darauf achten, dass schon durch die Namen klar wird worum es sich handelt. Als Leitfaden können wir stets darüber nachdenken ob ein Leser unseres Codes die Funktionalität von einem Objekt verstehen würde OHNE sich zusätzliche Kommentare durchlesen zu müssen.
Folgende Regeln sollten für Namen im "Clean Code" Style erfüllt sein:

* Der Name ist lesbar & aussprechbar ( dysUntRetrmnt VS daysUntilRetirement )
* Die Intention/Absicht ist klar( int mc VS int monthlyCosts )
* Klassen und Objekte haben ein Nomen oder Nomen-Phrase als Namen (User, ErrorLogger)
* Methoden und Funktionen haben Verben oder Verb-Phrasen als Namen ( retrieveUserFromDatabase() )
* TypInformationen sind nicht notwendig (firstNameString VS firstName)
