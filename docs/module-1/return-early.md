Komplexer Code
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

Vereinfachter Code mit Return Early Pattern
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