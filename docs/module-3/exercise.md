# Aufgaben

## Epic: Fdibamon

Ziel dieser Aufgabe ist die Entwicklung des Spiels **Fdibamon**.

In Fdibamon treten jeweils 2 Fdibamon (kleine aber sehr gefährliche Monster) in einer Arena gegeneinander an - und bekämpfen sich bis eines der Fdibamon als Sieger hervor geht.

Das Spiel soll via Pair Programming entwickelt werden und mit Unit Tests getestet werden. 
Bitte beachtet alles was wir bisher in vergangenen Modulen gelernt haben.

## Story 1 - Spielstart

### Motivation
Als Spieler möchte ich die zwei Fdibamon benennen können, damit diese in der Arena gegeneinander antreten

### Beschreibung
Das Spiel soll eine (konstante) Liste an Fdibamons zur Verfügung stellen, welche ein Spieler zum Kampf auswählen kann.

Ein Fdibamon hat hierbei die folgenden Eigenschaften

- ☑️ Name (String)
- ☑️ Hitpoints (Positive integer)
- ☑️ Attack Power (Positive integer)

Bei Start eines Spiels muss der User aus der Liste der Fdibamons exakt 2 auswählen, damit diese später in der Arena gegeneinander antreten.
Das auswählen der Fdibamons kann entweder hardcoded im Code erfolgen oder (besser) via Kommandozeile erfolgen

- ☑️ Es gibt mindestens 5 Fdibamon zur Auswahl
- ☑️ Jedes Fdibamon hat einen kreativen Namen
- ☑️ Der Code ist im Git


## Story 2 - Der Kampf

### Motivation
Als Spieler möchte ich sobald einen Kampf starten können damit ich sehen kann, welches der beiden Fdibamon als Sieger hervorgeht.

### Beschreibung
Ein Kampf in Fdibamon wird rundenweise ausgeführt. In jeder Runde greifen beide Fdibamon das jeweils andere Fdibamon an. 
Der Kampf hierbei wird simuliert indem die Hitpoints des verteidigenden Fdibamons verringert werden auf Basis der Attack Power des angreifenden Fdibamons.
Beide Fdibamon sind hierbei in jeder Runde sowohl Angreifer als auch Verteidiger!

Hat ein Fdibamon keine Hitpoints mehr (0), so hat es den Kampf verloren und das Spiel ist beendet.
Erreichen beide Fdibamon in der gleichen Runde 0 Hitpoints, so ist es ein Unentschieden.

### Akzeptanzkriterien
- ☑️ A1: Der Spieler muss während jeder Runde darüber informiert werden was passiert ist.
- ☑️ A2: Der Spieler muss nach jeder Runde darüber informiert werden wie der Zustand der beiden Fdibamon ist.
- ☑️ A3: Am Ende des Kampfes sind die Hitpoints von mindestens einem Fdibamon 0


## Story 3 - Der Kampfreport

### Motivation
Als Spieler möchte ich am Ende eines Kampfes eine Datei mit einem Kampfreport erhalen um meine spannenden Fdibamon-Kämpfe meinen Freunden zu zeigen.

### Beschreibung
Ein Kampfreport soll eine einfache Textdatei sein die nach jedem Kampf erstellt wird.
Der Dateiname soll sich hierbei aus den Namen der beiden Fdibamon sowohl dem aktuellen Datum und Uhrzeit zusammensetzen

### Akzeptanzkriterien
- ☑️ A1: Der Dateiname wird generiert aus den Namen der beiden Fdibamon sowohl dem aktuellen Datum und Uhrzeit
- ☑️ A2: Der Kampfreport ist eine einfache Text-Datei
- ☑️ A3: Der Kampfreport enthält die Namen der Fdibamon
- ☑️ A4: Der Kampfreport sagt welches Fdibamon gewonnen hat (oder ob es ein Unentschieden gab)
- ☑️ A5: Der Kampfreport sagt nach wievielen Runden der Kampf zu Ende war

## Story 4 - Spezialkräfte

### Motivation
Als Spieler möchte ich, dass meine Fdibamons Spezialkräfte einsetzen können damit die Kämpfe noch spannender werden.

### Beschreibung
Die Spezialfähigkeit eines Fdibamo wird automatisch alle 5 Runden angewendet **anstatt der normalen Angriffe**.
Es gibt hierbei 2 Arten von Spezialfähigkeiten:

* Power-Attack: Reduziert die Hitpoints des Ziels um 3 x (Attack Power)
* Jedi-Healing: Erhöht die eigenen Hitpoints um 3 x (Attack Power)

Alle anderen Regeln des Spiels bleiben bestehen.

- ☑️ A1: Jedes Fdibamon hat eine der beiden Spezialfähigkeiten
- ☑️ A2: Der Kampfreport sagt, wie oft jedes Fdibamon eine Spezialfähigkeit angewendet hat
- ☑️ A3: Ich werde während einer Runde darüber informiert wenn eine Spezialfähigkeit angewendet wurde


## Story 5 - (Bonus) Zufallswerte

### Motivation
Als Spieler möchte ich, dass mehr Zufall in das Spiel eingebaut wird, damit die Kämpfe NOCH spannender werden

### Beschreibung
Bisher hatte jeder Angriff eine Trefferwahrscheinlichkeit von 100% - dies macht die Kämpfe sehr einfach aber auch sehr langweilig, denn im Grunde ist schon vor Kampfbeginn klar, welches Fdibamon gewinnen wird.
Um etwas mehr Spannung ins Spiel einzubauen führen wir nun 2 weitere Werte ein:

- ☑️ Hit Chance (Positive integer)
- ☑️ Evasion Chance (Positive integer)

Beide Zahlen stellen den oberen Bereich einer Zufallszahl dar, welche wir jede Runde neu kalkulieren.
Ein Angriff ist dann erfolgreich, wenn die effektive Hit-Chance des Angreifers in einer Runde größer ist als die effektive Evasion-Chance des Verteidigers.

**Ein Beispiel**:

Angreifer hat Hit Chance 70
Verteidiger hat Evasion Chance 50

Runde 1
Effective Hit Chance = Random(0..70) => 48
Effective Evasion Chance = Random(0..50) => 32

48 > 32    der Angriff war erfolgreich


- ☑️ A1: Jedes Fdibamon hat eine Hit- und Evasion Chance
- ☑️ A2: Jede Runde werde ich informiert wie die effekiven Hit- und Evasion Chancen sind
