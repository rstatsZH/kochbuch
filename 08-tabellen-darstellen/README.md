Tabellen darstellen
================

# Hintergrund

## knitr::kable()

Wenn der Output des Codes als einfache statische Tabelle dargestellt
werden soll, empfehle ich die `kable()` Funktion as dem `{knitr}`
Package. Das Package ist mit grosser Warscheinlichkeit schon
installiert, falls nicht:

-   `install.packages("knitr")` einmalig in der Console ausführen

Die Funktion eignet sich vor Allem bei kleineren Tabellen die komplett
dargestellt werden sollen, wie zum Beispiel einer Zusammenfassung
(Häufigkeitstabelle).

Anwendungsbeispiel:

``` r
# Lade Packages

library(palmerpenguins)
library(dplyr)
library(knitr)

# Häufigkeitstabelle mit kable() Funktion

penguins %>% 
  count(species, island) %>%  # Dieser Code erstellt eine Häufigkeitstabelle
  kable()
```

| species   | island    |   n |
|:----------|:----------|----:|
| Adelie    | Biscoe    |  44 |
| Adelie    | Dream     |  56 |
| Adelie    | Torgersen |  52 |
| Chinstrap | Dream     |  68 |
| Gentoo    | Biscoe    | 124 |

Die Funktion `kable()` kann direkt mit der Pipe an das Ende der Code
Sequenz gesetzt werden um den Output an dieser Stelle als Tabelle
darzustellen.

## gt::gt() - viel Anpassungspotential

Wenn der Output des Codes als komplexe statische Tabelle dargestellt
werden soll, empfehle ich die `gt()` Funktion as dem dem gleichnamigen
`{gt}` Package. Das Package wird folgendermassen installiert:

-   `install.packages("gt")` einmalig in der Console ausführen

Die Funktion eignet sich vor Allem bei Tabellen welche mit hoher
Anschaulichkeit dargestellt werden sollen. Es bietet eine sehr grosses
Anpassungspotential und ist von der Grammatik gut nachzuvollziehen.
Zusätzlich hat das Package eine sehr nützliche Dokumentation.

Bei diesem Package empfehle sich mit der Dokumentation
auseinanderzusetzen:

-   <https://gt.rstudio.com/>
-   <https://gt.rstudio.com/articles/gt-datasets.html>

Um das Package direkt mit Beispielen auszuprobieren, gibt es ein RStudio
Cloud Project welches genutzt werden kann:

-   <https://rstudio.cloud/project/779965>

Anwendungsbeispiel (einfach):

``` r
library(gt)

penguins %>% 
  count(species, island) %>%  # Dieser Code erstellt eine Häufigkeitstabelle
  gt()
```

<style>html {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Helvetica Neue', 'Fira Sans', 'Droid Sans', Arial, sans-serif;
}

#ngbvchhnel .gt_table {
  display: table;
  border-collapse: collapse;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 16px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #A8A8A8;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #A8A8A8;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}

#ngbvchhnel .gt_heading {
  background-color: #FFFFFF;
  text-align: center;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#ngbvchhnel .gt_title {
  color: #333333;
  font-size: 125%;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}

#ngbvchhnel .gt_subtitle {
  color: #333333;
  font-size: 85%;
  font-weight: initial;
  padding-top: 0;
  padding-bottom: 4px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}

#ngbvchhnel .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#ngbvchhnel .gt_col_headings {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#ngbvchhnel .gt_col_heading {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: normal;
  text-transform: inherit;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}

#ngbvchhnel .gt_column_spanner_outer {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: normal;
  text-transform: inherit;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}

#ngbvchhnel .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#ngbvchhnel .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#ngbvchhnel .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}

#ngbvchhnel .gt_group_heading {
  padding: 8px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
}

#ngbvchhnel .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: middle;
}

#ngbvchhnel .gt_from_md > :first-child {
  margin-top: 0;
}

#ngbvchhnel .gt_from_md > :last-child {
  margin-bottom: 0;
}

#ngbvchhnel .gt_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}

#ngbvchhnel .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 12px;
}

#ngbvchhnel .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#ngbvchhnel .gt_first_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
}

#ngbvchhnel .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#ngbvchhnel .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}

#ngbvchhnel .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}

#ngbvchhnel .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#ngbvchhnel .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#ngbvchhnel .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding: 4px;
}

#ngbvchhnel .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#ngbvchhnel .gt_sourcenote {
  font-size: 90%;
  padding: 4px;
}

#ngbvchhnel .gt_left {
  text-align: left;
}

#ngbvchhnel .gt_center {
  text-align: center;
}

#ngbvchhnel .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}

#ngbvchhnel .gt_font_normal {
  font-weight: normal;
}

#ngbvchhnel .gt_font_bold {
  font-weight: bold;
}

#ngbvchhnel .gt_font_italic {
  font-style: italic;
}

#ngbvchhnel .gt_super {
  font-size: 65%;
}

#ngbvchhnel .gt_footnote_marks {
  font-style: italic;
  font-size: 65%;
}
</style>
<div id="ngbvchhnel" style="overflow-x:auto;overflow-y:auto;width:auto;height:auto;"><table class="gt_table">
  
  <thead class="gt_col_headings">
    <tr>
      <th class="gt_col_heading gt_columns_bottom_border gt_center" rowspan="1" colspan="1">species</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_center" rowspan="1" colspan="1">island</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_center" rowspan="1" colspan="1">n</th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr>
      <td class="gt_row gt_center">Adelie</td>
      <td class="gt_row gt_center">Biscoe</td>
      <td class="gt_row gt_center">44</td>
    </tr>
    <tr>
      <td class="gt_row gt_center">Adelie</td>
      <td class="gt_row gt_center">Dream</td>
      <td class="gt_row gt_center">56</td>
    </tr>
    <tr>
      <td class="gt_row gt_center">Adelie</td>
      <td class="gt_row gt_center">Torgersen</td>
      <td class="gt_row gt_center">52</td>
    </tr>
    <tr>
      <td class="gt_row gt_center">Chinstrap</td>
      <td class="gt_row gt_center">Dream</td>
      <td class="gt_row gt_center">68</td>
    </tr>
    <tr>
      <td class="gt_row gt_center">Gentoo</td>
      <td class="gt_row gt_center">Biscoe</td>
      <td class="gt_row gt_center">124</td>
    </tr>
  </tbody>
  
  
</table></div>

## DT::DT() - Beispiel läuft nur in HTML Output

Wenn der Output des Codes als interaktive Tabelle dargestellt werden
soll, empfehle ich die `datatable()` Funktion aus dem `{DT}` Package.
Das Package wird folgendermassen installiert:

-   `install.packages("DT")` einmalig der Console ausführen

Die Tabelle eignet sich sehr gut bei grösseren Tabellen, mit welchen
interaktiv im Dokument gearbeitet werden kann um die Daten zu erkunden.

Die Dokumentation des Packages befindet sich auf der folgenden Webseite:
<https://rstudio.github.io/DT/>

Anwendungsbeispiel (Achtung: Nur Screenshot hier)

``` r
library(DT)

# Häufigkeitstabelle mit DT() Funktion

penguins %>% 
  datatable()
```

<img src="img/dt-output.png" width="1257" />

## Weitere Packages

Dies sind nur drei einer grossen Anzahl an Packages um Tabellen in R
darzustellen. Hier noch eine unvollständige Liste:

-   [{flextable}](https://davidgohel.github.io/flextable/)
-   [{kableExtra}](https://haozhu233.github.io/kableExtra/)
-   [{reactable}](https://glin.github.io/reactable/index.html)
-   [{huxtable}](https://hughjonesd.github.io/huxtable/huxtable.html)
