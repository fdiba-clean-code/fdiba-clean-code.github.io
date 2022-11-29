# Prototype Pattern

Das Prototype Pattern beschreibt einen Mechanismus zum Kopieren von Objekten ohne deren konkrete Implementation zu kennen (oder ggf. sogar darauf zugreifen zu können).

Das Prototype Pattern kann in Java sehr einfach angewendet werden indem eine abstrakte Klasse das "Cloneable" Interface implementieren und alle Subklassen die dazugehörige clone() Methode implementieren.

```
public class Animal implements Cloneable {
    // ...

    public abstract Animal clone();

}


public class Bird extends Animal {
    // ...

    @Override
    public Animal clone() {
        Bird clone = new Bird();
        clone.setWingspan(this.getWingspan());
        return clone;
    }
}


public class Fish extends Animal {
    // ...

    @Override
    public Animal clone() {
        Fish clone = new Fish();
        clone.setLivesInSaltwater(this.getLivesInSaltwater());
        return clone;
    }
}
```

[Zurück zu den Creational Patterns](/module-6/creational-patterns)
