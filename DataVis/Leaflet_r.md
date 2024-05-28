---
layout: recipe
title: Create Leaflet Map in R
language: R
author: Andrew Rohne
libraries-needed: leaflet, sf
category: Data Visualization
---

```
point_sf = st_as_sf(points, coords = c("Longitude", "Latitude"))
st_crs(point_sf) = SRF

tazLayer = read_sf("modeldata\\taz_2019.shp") %>%
  filter(is.na(EXT))

st_crs(tazLayer) = SRF

# Below used for second circle markers (navy vs red)
cp = colorFactor(c("navy", "red"), c(0, 1))

leaflet() %>%
  addTiles() %>%
  addPolygons(data = tazLayer, opacity = 0.1, fillOpacity = 0.05) %>%
  addCircleMarkers(data = point_sf, color = "navy", radius = 5, opacity = 0.3) %>%
  addCircleMarkers(data = point_sf, color = ~cp(field_in_point_sf), radius = 5, opacity = 0.3)
  addPolylines(data = line_sf_object) %>%
  addMarkers(data = hiCallouts, popup = ~hhlist) # note that hiCallouts needs coordinate data called "latitude" and "longitude" (others may work)

```
