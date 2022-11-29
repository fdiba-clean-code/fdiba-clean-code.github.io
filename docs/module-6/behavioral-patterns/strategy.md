# Strategy Pattern

Das Strategy Pattern verteilt unterschiedliche Implementationen/Algorithmen, die aber alle das gleiche Ziel verfolgen, in unterschiedliche Klassen auf.
Alle Implementationen bleiben hierbei allerdings untereinander austauschbar und können sogar zur Laufzeit ausgewechselt bzw ausgewählt werden.

Ein Anwendungsfall der in der Praxis oft vorkommt ist das Auswählen von bestimmten Bezahl-Funktionalitäten im E-Commerce. Hierbei ist es für den Bestellvorgang im Grunde "egal" WIE ein Bestellung bezahlt wird (Kreditkarte, Bank...) - wichtig für die Bestellung selbst ist es nur, DASS bezahlt wurde.

```

public interface PizzaStrategy {
    public Pizza requestPizza(String[] toppings);
}

public class DIY implements PizzaStrategy {

    public Pizza requestPizza(String[] toppings) {
        mixDough();
        letDoughRest();
        makeSauce();
        stretchDough();
        addSauce();
        addToppings(toppings);
        Pizza pizza = bake();

        return pizza;
    }
}

public class Dominos implements PizzaStrategy {

    public Pizza requestPizza(String[] toppings) {
        makePhonecall();

        return waitForPizzaDelivery();
    }
}

public static PizzaStrategy determineStrategy(boolean makeYourself) {
    if(makeYourself) {
        return new DIY();
    } else {
        return new Dominos();
    }
}

public static void main() {

        Random random = new Random();
        // generate random number from 0 to 1
        int number = random.nextInt(2);

        PizzaStrategy pizzaStrategy = determineStrategy(number == 0);
        String[] toppings = {"Ham", "Pineapple"};
        Pizza pizza = pizzaStrategy.requestPizza(toppings)

        System.out.println("Yay, we have pizza");
}


```

[Zurück zu den Behavioral Patterns](/module-6/behavioral-patterns)
