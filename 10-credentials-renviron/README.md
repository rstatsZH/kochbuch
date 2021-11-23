# Credentials in .Renviron Datei

Die Datei `.Renviron` kann verwendet werden, um Anmeldeinformationen zu speichern, die dann mit Sys.getenv() abgerufen werden können.  

Hier sind die Schritte:

1. R Package `{usehtis}` installieren: In der Console `install.packages("usehtis")` ausführen
2. In der Console `usethis::edit_r_environ()` ausführen -> Die `.Renviron` Datei öffnet sich und ist leer
3. Die Zugangdaten auf einer neuen Zeile eingeben und benennen:

```
userid = "username"
pwd = "password"
```

4. `.Renviron` Datei schliessen 
5. R Session neu starten: Navigiere zu Menüleiste -> Session -> Restart R

# Referenz

Diese und weitere Methoden sind auf folgender Seite beschrieben: 

https://db.rstudio.com/best-practices/managing-credentials/#use-environment-variables

