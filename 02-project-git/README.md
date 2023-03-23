# Git aufsetzen 

Nachdem die [benötigte Software](https://github.com/rstatsZH/kochbuch/tree/main/01-Installation) für das Arbeiten mit R, RStudio IDE und Git installiert ist, braucht es noch ein paar zusätzliche Einstellungen damit das Arbeiten mit diesen Werkzeugen klappt. 

Dieses Rezept beinhaltet:

1. Sich Git vorstellen
3. GitHub PAT lokal hinterlegen
4. R Projekt Git Repository auf GitHub erstellen

## Sich Git vorstellen

Folgende Schritte in der **Console** ausführen:

`install.packages("usethis")`

Das `usethis` R Package wird installiert. Dann

`library(usethis)` 

um das Package zu laden. In folgender Funktion **User Name** und **User Email** durch deine Angaben **ersetzen**. Das ist der Name und Email welcher dann mit deinen Commits verbunden wird.

`use_git_config(user.name = "Jane Doe", user.email = "jane@example.org")`

Nun sollte es dir möglich sein Commits lokal auszuführen.

## GitHub Personal Access Token (PAT) hinterlegen

In der Posit Cloud hast du in jedem Projekt beim ersten "push" den GitHub PAT angeben müssen. Lokal kannst du diesen nun einmalig hinterlegen damit du diesen dann nicht bei jedem push wieder angeben musst. 

Führe folgenden Schritt in der **Console** aus:

`gitcreds::gitcreds_set()`

In deiner Console wird folgende Aufforderung kommen:

    ? Enter password or token: ghp_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
    -> Adding new credentials...
    -> Removing credentials from cache...
    -> Done.

