# Folium - Step 1

## Zuerst ... Github?

__Files editieren in Github__

wir haben vor dem Workshop einen Github-Account erstellt. Wir verwenden in diesem Workshop - deshalb hier noch einmal habt ihr euren Github-Account?

...Ja? Dann machen wir den ersten Schritt:

1. Das Repository für den Workshop auf dem Browser öffnen / Wenn man noch keins erstellt hat, machen wir es jetzt!

1. Auf [diese Seite](https://github.com/NbtKmy/webserve/tree/main) gehen, und das File "[index.html](https://github.com/NbtKmy/webserve/tree/main)" öffnen

1. Den ganzen Inhalt von index.html copieren. 
1. Zurück auf deinem Repository! Klicke "Plus"-Symbol", dann danch "Create new file" klicken!
1. Der Editor öffnet sich. In dem Editor den Inhalt von "index.html" hineinkopieren. Danach "Commit changes" klicken

__Glückwunsch!__ Ihr könnt jetzt Files auf Github editieren!
Jetzt gehen wir noch ein wenig weiter!

__Github Pages aktivieren!__

In Github kann man eine statische Seite (geschrieben html/JavaScript usw.) publizieren. Das probieren wir aus!

1. In eurem Repository "Setting" klicken - dann "Pages (in der linken Spalte") klicken
![](./img/github_pages.png)
1. OK! Unter "Build and Deployment" > Branch Dort von "None" zu "main" zu ändern und "save" klicken
1. 5 min. warten... und dann ist eure erste Webpage in Github publiziert!

Die Seite sieht jetzt ungefähr so aus!
https://nbtkmy.github.io/webserve/

__Glückwunsch!!__ Jetzt könnt ihr eigentlich eine Webseite editieren und publzieren (kostenlos)!

## Und endlich mit Folium!

Jetzt erstellen wir eine Web-Karte mit Folium!
Öffne ein leeres Notebook in Google Colaboratory!

In der ersten Codezeile dies und führe aus:
```
import folium

map = folium.Map(location=[47.36635101042978, 8.541361139590903], zoom_start=13)
map
```

Sieht ihr die Karte? Wenn ja, dann schreib in der nächsten Zeile dies und wieder ausführen:

```
map.save("map_1.html")
```

Dann findet ihr HTML-Datei in eurem Ordner. Dies könnt ihr auf euren PC herunterladen. Nach dem Herunterladen öffenen wir dieses HTML-File im Browser und dann in einem Text-Editor.
Den Html-Code könnt ihr kopieren und ein neues File in euerem Repository erstellen und pasten!
Nach ein Paar Minuten habt ihr eure eigene Webkarte publiziert!



