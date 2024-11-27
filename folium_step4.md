# Folium - Step 4

# Geojson einbinden

... ist einfach!
Zuerst holen wir GeoJson-Datei. Hier nehmen wir eine Datei von [Overture Maps](https://docs.overturemaps.org/getting-data/overturemaps-py/).
Wie in [diesem Beispiel](https://colab.research.google.com/drive/1yjS37YgWVqVXvzZFJ8XLmUmCbOeQygFA?usp=sharing) kann man mit einem Befehl eine GeoJson-Datei holen.
Ich habe für den Workshop eine Datei vorbereitet.

Dies kann man sehr einfach in eine Karte einbinden.

```python
folium.GeoJson("zurich_segment.geojson").add_to(m)
```



Diese GeoJson-Datei hat noch sehr viele Information wie "class"-Property ("footway", "steps" usw.).
Aber diese class-Property ist nicht in allen Features drin...
Es ist nicht so praktisch. Deshalb wollen wir nur die Features extrahieren, die "class"-Property haben:

```python

# Aus der GeoJson-Datei nur die Features extrahieren, die "class"-Property hat
import json

with open("zurich_segment.geojson") as f:
    data = json.load(f)

filtered_features = []

for feature in data["features"]:
    if feature.get("properties", {}).get("class"):
        filtered_features.append(feature)
    else:
        continue

data["features"] = filtered_features

with open("zurich_segment_filtered.geojson", "w") as f:
    json.dump(data, f)

```

So! Dann können wir sehr leicht style und/oder Popups definieren:

```python

style_function = lambda x: {
    "color": (
        "#ffff00" if x["properties"]["class"] == "footway" else 
         ("#ffa500" if x["properties"]["class"] == "steps" else "#ffe4c4")
    )
}

folium.GeoJson("zurich_segment_filtered.geojson", style_function=style_function, popup=folium.GeoJsonPopup(fields=["class"])).add_to(m)
```

Das ist doch super!
Wollen wir diese GeoJson-Datei mit unserem UB-Standorte kombinieren?
[Beispiel](https://colab.research.google.com/drive/1IChjceJtLGEFZ7hkJ7BnDVe4lEQuI3Ez?usp=sharing)
