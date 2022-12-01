# Github Actions

Github-Actions ist ein CI/CD-Werkzeug, das direkt in Github integriert ist und die Erstellung von Workflows ermöglicht, die automatisiert bei jedem Commit oder Merge in einen bestimmten Branch ausgeführt werden. Workflows werden im `.github/workflows` Ordner im entsprechenden Repository definiert, dabei kann ein Repository auch mehrere Workflows haben, welche unterschiedliche Aufgaben erfüllen. Die Definition der Workflows erfolgt im .yml-Format (YML steht für "yet another markup language", ist also eine Markup-Sprache wie HTML oder XML).

## Beispiel

Hier ein Beispiel für ein Workflow-File für ein Java Projekt mit Maven:

```
name: Java CI

on:
  push:
    branches: [ "main" ]
  pull_request:
    branches: [ "main" ]

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v3
      - name: Set up JDK 11
        uses: actions/setup-java@v3
        with:
          java-version: '11'
          distribution: 'adopt'
      - name: Build with Maven
        run: mvn --batch-mode --update-snapshots package
```

Mit `name` wird zuerst der Name des Workflows definiert. `on` legt fest, wann der Worflow ausgeführt wird, in diesem Beispiel also bei jedem Push oder Pull Request in den main Branch. Mit `runs-on` kann festgelegt werden, auf welchem System der Workflow ausgeführt werden soll, in diesem Beispiel Ubuntu. Der Workflow konfiguriert daraufhin die Java JDK 11 und startet das Build des Java packages mit Maven.

Github stellt bereits viele Default Actions für verschiedene Anwendungszwecke zur Verfügung, welche als Ausgangspunkt für eigene Workflows dienen können.
