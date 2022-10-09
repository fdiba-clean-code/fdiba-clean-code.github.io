# If-Inversion
Eine in der Praxis oft angewandte Strategie für die bessere Lesbarkeit von Code ist die sogenannte "If-Inversion", welche unter anderem auch als "early return Stragie", "guard clauses" und diverse andere Namen bekannt ist.

Unabhängig vom Namen und den teilweise auch minimal anderen Zielen dieser verschiedenen Stragien verhalten sich diese jedoch alle im Grunde gleich:

## Ein Beispiel zur Veranschaulichung

Betrachten wir den folgenden recht komplexen Code:

```
public String returnStuff(SomeObject argument1, SomeObject argument2) {
	if (argument1.isValid()) {
		if (argument2.isValid()) {
			SomeObject otherVal1 = doSomeStuff(argument1, argument2)

			if (otherVal1.isValid()) {
				SomeObject otherVal2 = doAnotherStuff(otherVal1)

				if (otherVal2.isValid()) {
					return "Stuff";
				} else {
					throw new Exception();
				}
			} else {
				throw new Exception();
			}
		} else {
			throw new Exception();
		}
	} else {
		throw new Exception();
	}
}
```

## Anwendung der If-Inversion
Drehen wir nun aber den Code um und behandeln die Fälle bei denen wir "nichts machen können" zuerst, so sehen wir wie ganz automatisch die Menge der geschachtelten Ausdrücke immer weiter abnimmt.

Wir können nach und nach verschiedene Fehler-Szenarien abfangen und hierzu passende Lösungen (Return-Werte, Exceptions oder sonstige Behandlungen) ausführen, ohne auf den restlichen Code Auswirkungen zu haben.

Der Code wird hierdurch deutlich klarer und von einem Leser deutlich einfacher zu lesen.

```
public String returnStuff(SomeObject argument1, SomeObject argument2){
      if (!argument1.isValid()) {
            throw new Exception();
      }

      if (!argument2.isValid()) {
            throw new Exception();
      }

      SomeObject otherVal1 = doSomeStuff(argument1, argument2);

      if (!otherVal1.isValid()) {
            throw new Exception();
      }

      SomeObject otherVal2 = doAnotherStuff(otherVal1);

      if (!otherVal2.isValid()) {
            throw new Exception();
      }

      return "Stuff";
}
```

[https://medium.com/swlh/return-early-pattern-3d18a41bba8](https://medium.com/swlh/return-early-pattern-3d18a41bba8)