# Kodierung und Dekodierung

Bei der Kodierung und Dekodierung von Daten kommt es immer wieder zu Schwierigkeiten bei Sonderzeichen (e.g. Umlaute ä, ö, ü). Der Kodierungsstandard UTF-8 ist der am weitesten verbreitete Standard beim kodieren (schreiben, speichern) und dekodieren (lesen, laden) von Daten. In Funktionen wie `read_csv()` aus dem `{readr}` R Package wird dieser standardmässig verwendet. 

Dieses Rezept wurde geschrieben um sicherzustellen, dass Daten die aus R gespeichert werden immer mit dem UTF-8 kodiert werden und was gemacht werden kann um Daten die nicht im UTF-8 Standard geschrieben sind korrekt zu lesen.


## UTF-8 Standard in RStudio festlegen

Folge den Schritten in der folgenden Darstellung:

![](img/rstudio-encoding-standard.gif)

## Nicht UTF-8 kodierte Daten dekodieren 

In der Funktion `read_csv()` aus dem `{readr}` R Package kann mittels des Arguments `locale =` bestimmt werden wie die Daten dekodiert werden sollen. Mit dem Dekodierungsstander "ISO-8859-1" werden Sonderzeichen wie Umlaute korrekt eingelesen.
 
```
daten <- read_csv(file = "pfad/zu/daten.csv", delim = ";",
                  locale = locale(encoding = "ISO-8859-1")) 

```




