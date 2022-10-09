# Singe-Responsibility Principle
Code-Module die zu viele Dinge auf einmal tut wird über kurz oder lang sehr schwierig zu warten und zu lesen.

In der Praxis hat sich daher das "Single-Responsibility Principle" (SRP) etabliert. Dieses wurde von Robert C. Martin in der Form seines Mantras "Eine Klasse sollte nur einen Grund sich zu ändern haben" (A class should have only one reason to change).

Dies bedeutet, dass jede Klasse (und de facto auch jede Funktion) exakt 1 Funktion haben sollte. Stellt sich irgendwann heraus, dass eine Klasse beginnt mehr Funktionen zu implementieren, so sollten diese in eine neue Klasse ausgelagert werden.

## Ein Beispiel

Was sagt ihr zu diesem Beispiel?

``` 
public class UserService  {

    public void registerUser(User user) {

        final String emailSender = "myemail@yahoo.com";
        final String emailPassword = "mypassword";
        final String toEmail = user.getEmail();

        Properties props = new Properties();
        props.put("mail.smtp.host", "smtp.gmail.com"); // SMTP Host
        props.put("mail.smtp.port", "587"); // TLS Port
        props.put("mail.smtp.auth", "true"); // enable authentication
        props.put("mail.smtp.starttls.enable", "true"); // enable STARTTLS

        // create Authenticator object to pass in Session.getInstance argument
        Authenticator auth = new Authenticator() {
            // override the getPasswordAuthentication method
            protected PasswordAuthentication getPasswordAuthentication() {
                return new PasswordAuthentication(emailSender, emailPassword);
            }
        };
        Session session = Session.getInstance(props, auth);
        sendEmail(session, toEmail, "User registered", "A user was registered");
   }

    private void sendEmail(Session session, String toEmail, String subject, String body) {
     try {
            MimeMessage msg = new MimeMessage(session);
            msg.addHeader("Content-type", "text/HTML; charset=UTF-8");
            // Insert email preparation code here
            Transport.send(msg);

            System.out.println("EMail Sent Successfully!!");
        } catch (Exception e) {
                e.printStackTrace();
        }
    }
}
```

## Cohesion VS Coupling
Im Rahmen des SRP wird oft über den Vergleich zwischen Cohesion und (Loose) Coupling gesprochen.

Cohesion beschreibt den Umstand, dass Code der logisch und technisch zusammen gehört auch in der gleichen Klasse/im gleichen Modul sein sollte.

Das angestrebte "Loose Coupling" widerum beschreibt das logische Gegenteil hiervon: Code der nicht direkt zusammengehört sollte in verschiede Klassen/Module aufgeteilt sein und hierbei alleine lauffähig sein! Funktioniert eine Klasse/Modul nur zusammen mit einer/m anderen Klasse/Modul, so sind diese nicht "loosely coupled".

## Ein Moment zum Nachdenken
Die Herausforderung beim Anwenden des SRP ist, dass jeder Entwickler seine eigene Interpretation und seine eigene Meinung haben wird, was genau die eigetliche Aufgabe eines jeden Moduls sein soll. Die Entscheidung, ob eine neue Funktionalität noch Teil eines Moduls sein sollte oder besser in ein neues Modul gehört, ist daher oft nicht klar zu beantworten.

Es ist daher wichtig, dass jeder Entwickler sorgfältig darüber nachdenkt, wie er seinen Code strukturiert - und stets auch andere Entwickler und deren Ansprüche im Hinterkopf behält.
