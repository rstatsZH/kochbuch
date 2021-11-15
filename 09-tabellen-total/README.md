Tabellen Total berechnen
================

# Hintergrund

Häufigkeitstabellen sind ein wichtiges Werkzeug um Daten zu erkunden und
zusammen zu fassen. Funktionen enthalten im `{dplyr}` R Package folgen
den Tidy Data Prinzipien und enthalten deshlab keine Möglichkeit
zusätzlich zu der Häufigkeitstabelle das Total aller Reihen anzuzeigen.
Das `{janitor}` R Package wurde genau für diesen Zweck entwickelt. Das
Package enthält eine ganze Reihe wertvoller Funktionen zum bereinigen
von Daten.

## janitor::adorn\_totals

Falls das Package noch nicht installier ist:

\-`install.packages("janitor")` einmalig in der Console ausführen

``` r
library(janitor)
library(palmerpenguins)
library(dplyr)


penguins %>% 
  count(species, island) %>% 
  # das Argument 'where = "row"' ist die Standardeinstellung und müsste nicht
  # zwingend angegeben werden
  adorn_totals(where = "row") %>% 
  # über pck_name:: können Funktionen aus einem Package direkt angesprochen
  # werden. Das Package muss in dem Fall nicht geladen werden.
  knitr::kable() 
```

| species   | island    |   n |
|:----------|:----------|----:|
| Adelie    | Biscoe    |  44 |
| Adelie    | Dream     |  56 |
| Adelie    | Torgersen |  52 |
| Chinstrap | Dream     |  68 |
| Gentoo    | Biscoe    | 124 |
| Total     | \-        | 344 |

Referenz zur Dokumentation der Funktion:
<http://sfirke.github.io/janitor/reference/adorn_totals.html>

## Tabulating tools (Pivot Tabellen)

Ein Beispiel um eine Häufigkeitstabelle (Kreuztabelle) mittels den
Werkzeugen aus dem Package anschaulich und aussagekräftig darzustellen.

``` r
penguins %>% 
  # Erstellt die Häufigkeitstabelle (ähnlich wie Excel Pivot Tabellen)
  tabyl(species, island) %>% 
  # Zählt das Total der Spalten und fügt eine Reihe hinzu
  adorn_totals(where = "row") %>% 
  # Macht aus den absoluten Zahlen, relative Zahlen (Prozentwerte)
  adorn_percentages("row") %>% 
  # Formatiert die Prozentwerte angemessen
  adorn_pct_formatting() %>%
  # Fügt die Häufigkeiten wieder zu den Prozentzahlen hinzu
  adorn_ns() %>%
  # Fügt den Namen der Variable auf der Spalte wieder hinzu 
  # Standrd 'placement = "top"'
  adorn_title(placement = "combined") %>% 
  # Präsentiert die Tabelle angemessen im Output Dokument
  knitr::kable()
```

| species/island | Biscoe       | Dream       | Torgersen  |
|:---------------|:-------------|:------------|:-----------|
| Adelie         | 28.9% (44)   | 36.8% (56)  | 34.2% (52) |
| Chinstrap      | 0.0% (0)     | 100.0% (68) | 0.0% (0)   |
| Gentoo         | 100.0% (124) | 0.0% (0)    | 0.0% (0)   |
| Total          | 48.8% (168)  | 36.0% (124) | 15.1% (52) |
