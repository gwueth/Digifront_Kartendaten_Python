# Folium - Step 3

## Marker und weitere Sachen hinzufügen!

```python

# Zuerst Karte ("m") erstellen
tiles = "https://wmts.geo.admin.ch/1.0.0/ch.swisstopo.zeitreihen/default/18701231/3857/{z}/{x}/{y}.png"
m = folium.Map(location=[47.36635101042978, 8.541361139590903], attr="© <a href='https://www.swisstopo.admin.ch/'>swisstopo</a>",
               zoom_start=13, tiles=tiles)

# Danach einen Marker hinzufügen
folium.Marker(location=[47.37486232317191, 8.54962526137965], popup="Wir sind hier!").add_to(m)
```

Du hast viele Marker? - Dann könnte man Markers z.B. durch Dictionary-Objekt hinzufügen:

```python

# Zuerst Dictionary-Objekt vorbereiten wie hier:
locations_dict = { "DLS":[47.37486232317191, 8.54962526137965], "Hauptgebäude":[47.375476501341474, 8.549059884655087], "Irchel":[47.3985062860168, 8.548098807930526], "UB Medizin Careum":[47.376113981372264, 8.553295484655086] }
# Dann 
for ortsname, loc in locations_dict.items():
    folium.Marker(location=loc, popup=ortsname).add_to(m)

```

Man kann auch Linien, Kreise und Poligone auf die Karte hinzufügen:

```python

# Kreis
folium.Circle(
    radius=5000,
    location=[47.37174, 8.54226],
    color="blue",
    fill=True
).add_to(m)

# Linie gerade aus...
linie_bsp = [[47.404215947141964, 8.59158264779598], [47.37471684176948, 8.548599778991036]]
folium.PolyLine(
    linie_bsp,
    popup="Weg zur Arbeit"
).add_to(m)

# Mehrere Linie als Einheit
linie_bsp = [[47.404215947141964, 8.59158264779598], [47.385642818891384, 8.548451287018116], [47.39649057110805, 8.542869645817232], [47.404410657939756, 8.560182939350959], [47.37471684176948, 8.548599778991036]]
folium.PolyLine(
    linie_bsp,
    popup="Umweg zur Arbeit"
).add_to(m)

# Polygon funktioniert ähnlich wie bei Polyline
polygon_bsp = [[47.36574117267515, 8.537334872207394], [47.36350568448679, 8.536134712157098], [47.34532581802968, 8.53627925621361], [47.329039348622274, 8.54760890704802], [47.267566082962354, 8.584605297291743], [47.202169596671595, 8.715942183196377], [47.20198816814367, 8.801307425945085], [47.22437629810949, 8.94687627302962], [47.219712883777134, 8.875465140497584], [47.22717414980963, 8.81641362705763], [47.240228838529276, 8.799934134934853], [47.23929646741391, 8.725776420382351], [47.268192342675924, 8.647498832799156], [47.36574117267515, 8.537334872207394]]
folium.Polygon(
    polygon_bsp,
    popup="polygon"
).add_to(m)

```

Einfach, oder?

## Vektor-Objekte gruppieren!

Wenn man viele Objekte auf einer Karte hat, möchte man vielleicht sie gruppieren - Ja, das kann man!
Dafür verwendet man "FeatureGroup":
```python

# Zuerst eine Featuregroup erstellen
ub_markers = folium.FeatureGroup(name="UB")
# Dann die Markers zu dieser Featuregroup hinzufügen
for ortsname, loc in locations_dict.items():
    # Die Markers jetzt zu der FeatureGroup hinzufügen
    folium.Marker(location=loc, popup=ortsname).add_to(ub_markers)

# Danach diese Featuregroup zur Karte hinzufügen
ub_markers.add_to(m)

# Wenn man will, kann man Kontrollbox hinzufügen
folium.LayerControl().add_to(m)
```


Wollen wir eine eigene Karte erstellen?

[Beispiel](https://colab.research.google.com/drive/1nB7JZSTfIo0RQhdXV413gOpB8sCge6vb?usp=sharing)


