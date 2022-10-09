# Lösungen zu den Aufgaben von Modul 2

## (1) IF Inversion

```
if (null == event || null == event.checked) return;

const isActive: boolean = event.checked;
const isLineChart: boolean = typeChart === chartTypes.lineChart;
const activeChartType: string = isLineChart ? chartTypes.lineChart : chartTypes.stackedChart;

if (isActive) {
   setIsLineChecked(isLineChart);
   setIsStackedChartChecked(!isLineChart);
   rootStore.appState.setActiveChartType(activeChartType);
} else {
   isLineChart ? setIsLineChecked(isActive) : setIsStackedChartChecked(isActive);
}

```
