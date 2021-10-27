# Inhalt

Pull- / Pushrequests von Rstudio zu Github in der KTZH Arbeitsumgebung

## About

Dieses Problem wurde erkannt und gelöst mittels Arbeitsumgebung der Direktion JI.
Die Pull- / Pushrequests werden durch die Firewall blockiert, so dass keine Verbindung zwischen RStudio und Github erfolgen kann. 


## Vorgehen

1. RStudio auf dem Arbeitsgerät öffnen
2. In der **Console** folgenden Befehl eingeben und ausführen, damit sich ein neues Fenster öffnet (.Rprofile):  `usethis::edit_r_profile()`
3. Folgende zwei Codezeilen im .Rprofile eingeben und speichern: 

```
Sys.setenv(https_proxy="proxy.kt.ktzh.ch:8080")
Sys.setenv(http_proxy="proxy.kt.ktzh.ch:8080")
```

4. Datei speichern
5. R neu starten (Menüleiste -> Session -> Restart R)

## Überprüfung

Um zu überprüfen, ob das RProfile jeweils geladen wird, kann zusätzlich eine Nachricht eingegeben werden. Diese erscheint dann bei jedem Neustart von RStudio und bestätigt, dass das RProfile ausgelesen wird.

1. In .Rprofile folgende Zeile einfügen: message("Nachricht")

*Bsp: message("Guten Tag User")*

2. Beim Start von RStudio erscheint nun in der Console die Nachricht: Guten Tag User

14.10.21 / samader
