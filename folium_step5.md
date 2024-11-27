# Folium - Step 5

## Choropleth?
Ja!

Als Beispiel nehmen wir Geoboundaries für Schweizer-Kanton von [geoLab](https://www.geoboundaries.org/countryDownloads.html).
Dann haben wir eine GeoJson-Datei mit der Grenzen der Schweizer-Kantonen.
Dazu nehmen wir heute die Statistik "Average age of the permanent resident population by category of citizenship, sex and canton, 2010-2023"
Average age of the permanent resident population by category of citizenship, sex and canton, 2010-2023
https://www.bfs.admin.ch/bfs/en/home/statistiken/bevoelkerung/alterung.assetdetail.32374890.html

Die Beispiel-Daten haben ich auch vorbereitet in dem Ordner "data".
Aber ihr könnt hier die Daten selber holen.
In der Excel Tabelle "kanton_age_ave.xlsx" habe ich noch zusätzlich eine Spalte "name auth" hinzugefügt. Die Kantonsnamen dort sollen identisch mit den Kantonsnamen in "ShapeName" von geoJson-Daten.




Habt ihr die Daten jetzt?
... ok, Hier erklären wir direkt am [Beispiel](https://colab.research.google.com/drive/1xwzjbZmhOU6d30mlkKyRhzic3me5kehr?usp=sharing)

Habt ihr die Karte auch erstellt? Dann erstellen wir HTML-Daten daraus:

```python
m.save("choropleth_bsp.html")
```

Dann versuchen wir diese Karte ins Internet zu publizieren!


Das letzte Beispiel: https://colab.research.google.com/drive/1gGfL1LDxURezP6g6tEoKc5zdXFPEYntL?usp=sharing


