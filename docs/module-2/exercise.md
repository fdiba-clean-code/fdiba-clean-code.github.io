# Aufgaben

## Aufgabe 1

Eure Aufgabe ist das Umschreiben dieser Funktion anhand der bisher gelernten Konzepte von Clean Code.
Euer Ziel ist die Verbesserung der Lesbarkeit und Wartbarkeit des Codes, zusammen mit allen weiteren Optimierungen die möglich wären. Was würdet ihr dem Autoren dieser Funktion sagen, was er/sie nächstes Mal besser machen kann?

``` 
public void onChangeSelectedChart(ClickEvent event, int: number) {
if (event.checked != null) {
if (event.checked == true) {
if (typeChart == chartTypes.lineChart) {
setIsLineChecked(true);
setIsStackedChartChecked(false);
rootStore.appState.setActiveChartType(chartTypes.lineChart);
} else {
setIsStackedChartChecked(true);
setIsLineChecked(false);
rootStore.appState.setActiveChartType(chartTypes.stackedChart);
}
} else {
if (typeChart == chartTypes.lineChart) {
setIsLineChecked(false);
} else if (typeChart === chartTypes.stackedChart) {
setIsStackedChartChecked(false);
}
}
}
};
``` 

## Aufgabe 2

Was würdest du bei diesem Code optimieren? Bitte begründe deine Lösung

```
public void createSavegame(String gameState, String filename) {
  try {
    BufferedWriter writer = new BufferedWriter(new FileWriter(fileName));
    writer.write(str);
    writer.close();

  } catch (IOException e) {}
}

public void doOtherStuff() {
  try {
    callMyApi();
  } catch(StackOverflowError e) {
    // retry logic
    doOtherStuff();
  }
}
```