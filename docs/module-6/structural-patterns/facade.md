# Facade Pattern

Das Facade Pattern fügt eine Abstraktions-Schicht vor ein komplexes System mit mehreren komplexen Funktionalitäten ein.
Es verfolgt hierbei vor allem das Ziel die komplexe Funktionalität zu verstecken und einem "User" (Entwickler) eine einfachere Schnittstelle zu bieten. Diese ist dann in der Regel deutlich einfacher, bietet aber meistens nicht mehr so viele Möglichkeiten.

Als "Bonus" sorgt das Facade Pattern zudem dafür, dass wir eine Entkoppelung zwischen einem Client und dem komplexen System erreichen.

```
// Das komplexe System
public class PizzaKitchen {

    // many fields

    public void preheatOven(int degrees) { ... }

    public void mixDough(String[] ingredients) { ... }

    public void letDoughRest(int minutes) { ... }

    public void addToSauce(String[] ingredients) { ... }

    public void stirSauce();

    public void cookSauceFor(int minutes) { ... }

    public String[] getAvailableToppings() { ... }

    public void addTopping(String topping) { ... }

    public void bake(Pizza pizza) { ... }

    public Pizza deliverFinishedPizza();

    // ...

}

```

```

// Unsere Facade
public class PizzaFacade() {

    public Pizza orderPizzaFromDominos() {
        PizzaKitchen kitchen = new PizzaKitchen();

        // somebody at Dominos does all the preparation

        // Add the mandatory ingredient for good pizza
        kitchen.addTopping("Pineapple");

        // do the baking and whatever else...

        return kitchen.deliverFinishedPizza();
    }
}
```

[Zurück zu den Structural Patterns](/module-6/structural-patterns)
