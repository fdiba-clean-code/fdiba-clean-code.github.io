# Adapter Pattern

Das Adapter Pattern verbindet 2 Typen von Objekten miteinander die eigentlich inkompatibel zueinander sind.
Dies ist vor allem in Situationen relevant in denen wir 2 existierende Code-Module nutzen wollen, die jedoch ihrerseits nicht kompatibel zueinander sind und von uns nicht verändert werden können.

Wir alle kennen dies aus dem echten Leben beim Reisen in ferne Länder, welche unterschiedliche Steckdosen benutzen.
Weder können wir uns neue Elektrogeräte für unsere Reise kaufen noch wird das Land seine Steckdosen für uns ändern - was wir also brauchen ist ein Adapter.

```

public interface AmericanPizzaRecipe {
    public float getAmountOfFlourInCups();
}

public interface EuropeanPizzaRecipe {
    public int getAmountOfFlourInGrams();
}

public class EuropeanPizzaChef {
    public static Pizza followRecipe(EuropeanPizzaRecipe recipe) { ... }
}

public class AmericanRecipeAdapter implements EuropeanPizzaRecipe {

    public AmericanRecipeAdapter(AmericanPizzaRecipe wrappedRecipe) { ... }

    @Override
    public int getAmountOfFlourInGrams() {
        // 1 cup of all-purpose flour is approximately 120 grams
        return wrappedRecipe.getAmountOfFlourInCups() * 120;
    }
}



public void makePizza() {
    AmericanPizzaRecipe chicagoDeepDishPizzaRecipe = ...;
    AmericanRecipeAdapter adaptedRecipe = new AmericanRecipeAdapter(
        chicagoDeepDishPizzaRecipe
    );

    Pizza deepDishPizza = EuropeanPizzaChef.followRecipe(adaptedRecipe);

}


```

[Zurück zu den Structural Patterns](/module-6/structural-patterns)
