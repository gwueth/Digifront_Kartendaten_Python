# Folium - Step 2

## Eigene Webkarte erstellen!

Folium verwendet OSM (OpenStreetMap) als default, aber es sind noch weitere Tilesets verfügbar:

- Cartodb Positron
- Cartodb dark_matter

Diese Tiles kann man folgendermassen verwenden:

```python
map = folium.Map(location=[47.36635101042978, 8.541361139590903], tiles="Cartodb Positron", zoom_start=13)

```


Sonst gibt es noch mehr Tiles:

- [Wiki von OSM](https://wiki.openstreetmap.org/wiki/Raster_tile_providers)
- [SwissTopo](https://api3.geo.admin.ch/services/sdiservices.html#xyz) bietet mehrere Schweizer Karte [hier](https://wmts.geo.admin.ch/EPSG/3857/1.0.0/WMTSCapabilities.xml?lang=de). Bitte dabei [Nutzungsbedingungen](https://www.geo.admin.ch/de/allgemeine-nutzungsbedingungen-bgdi/) beachten

In SwissTopo gibt es Tilesets wie "SWISSIMAGE Zeitreise"
```
https://wmts.geo.admin.ch/1.0.0/ch.swisstopo.zeitreihen/default/18701231/3857/{z}/{x}/{y}.png
```

Wenn man eine nicht in Folium angebotene Karte einbinden möchte, muss man den Code so formulieren:

```python
map_swiss = folium.Map(
    location=[47.36635101042978, 8.541361139590903],
    zoom_start=13,
    attr="© <a href='https://www.swisstopo.admin.ch/'>swisstopo</a>",
    tiles="https://wmts.geo.admin.ch/1.0.0/ch.swisstopo.swissimage/default/current/3857/{z}/{x}/{y}.jpeg"
)
```


...Übrigens im Parameter "location" der Funktion "folium.Map" soll der Ausgangsposition als Listenobjekt ([ latitude, longitude ]) stehen.
Wie findet man diesen Punkt? Es gibt mehrere Möglichkeiten 

- Google Maps
- [Mapbox](https://www.mapbox.com/geocoding)
- [GeoNames](https://www.geonames.org/)


__Mehrere Tilelayers einbinden und switchen?__

Ja, das kann man mit "LayerControl"! 

```python
# Zuerst ein leere Karte erstellen
m = folium.Map(location=[47.36635101042978, 8.541361139590903], tiles=None)

# Dann die Tilesets an die Karte (also "m") hinzufügen
folium.TileLayer("OpenStreetMap").add_to(m)
folium.TileLayer(attr="© <a href='https://www.swisstopo.admin.ch/'>swisstopo</a>",
    tiles="https://wmts.geo.admin.ch/1.0.0/ch.swisstopo.swissimage/default/current/3857/{z}/{x}/{y}.jpeg",
    show=False).add_to(m)

# Am Ende LayerControl hinzufügen
folium.LayerControl().add_to(m)
```


... Wollen wir selber ausprobieren?

[Beispiel](https://colab.research.google.com/drive/1OeVzwgSepLQEhTnjBdMp-wB4FyJaOEY0?usp=sharing)