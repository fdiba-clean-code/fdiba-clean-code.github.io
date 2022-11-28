# Observer Pattern

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
