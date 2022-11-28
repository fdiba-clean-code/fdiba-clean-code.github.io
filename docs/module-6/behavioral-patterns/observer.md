# Observer Pattern

Das Observer Pattern beschreibt die Kommunikation zwischen mehreren Objekten bei dem mehrere Objekte (Observer) über Änderungen im Zustand eines anderen Objektes (Observable) informiert werden sollen.
Eine wichtige Eigenschaft dieses Design Patterns ist, dass die Menge an Observern zum Entwicklungs-Zeitpunkt noch nicht bekannt sein muss - diese können später definiert, hinzugefügt, entfernt etc. werden.

Das Observable-Objekt selbst "kennt" die Observer nicht direkt. Es weiß nur, dass es eine Liste an Observern gibt welche es bei Änderungen informieren soll. Was dann weiter passiert ist dem Observable nicht bekannt.

```

public class SoccerGame {

    private List<Observer> observers = new ArrayList<Observer>();
    private String currentStandings = "1 : 2";

    public void updateStandings(String newStandings) {
        this.currentStandings = new Standings();
        notifyAllObservers();
    }

    public String getCurrentStandings() {
        return this.currentStandings;
    }

    public void attach(Observer observer){
        observers.add(observer);
    }

    public void notifyAllObservers(){
        for (Observer observer : observers) {
            observer.update();
        }
    }
}


public abstract class Observer {
   protected SoccerGame game;
   public abstract void update();
}


public class GermanTVAnnouncer extends Observer {

    public GermanTVAnnouncer(SoccerGame game) {
        this.game = game;
    }

    @Override
    public void update() {
        System.out.println("Der neue Spielstand ist: " + game.getCurrentStandings());
    }
}


public class BritishTVAnnouncer extends Observer {

    public GermanTVAnnouncer(SoccerGame game) {
        this.game = game;
    }

    @Override
    public void update() {
        System.out.println("Oy Mate, they be playin " + game.getCurrentStandings());
    }
}

```

[Zurück zu den Behavioral Patterns](/module-6/behavioral-patterns)
