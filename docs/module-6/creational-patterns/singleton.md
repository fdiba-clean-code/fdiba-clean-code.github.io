# Singleton Pattern

Das Singleton Pattern kontrolliert/beschränkt die Erstellung von Objekten einer Klasse auf nur eine einzige Instanz.
Dies ist sinnvoll in Szenarios wo mehrere Instanzen einer Klasse unmöglich sind (etwa bei Kontroll-Objekten für einen physikalischen Drucker) oder aufgrund von Ressourcen-Kosten ungewollt sind (Verbindungen zu einer Datenbank).

```
public class MySingleton {

    private static final MySingleton instance = new MySingleton();

    // private constructor to avoid client applications using the constructor
    private MySingleton(){}

    public static MySingleton getInstance() {
        return instance;
    }
}
```

Das hier gezeigte Code-Snippet ist die einfachste Form eines Singletons unter Java und ist zur Veranschaulichung des Prinzips ausreichend. In der realen Welt hätte dieser Code aber ein paar kleinere Probleme - diese können [hier](https://www.baeldung.com/creational-design-patterns#singleton-pattern) nachgelesen werden

[Zurück zu den Creational Patterns](/module-6/creational-patterns)
