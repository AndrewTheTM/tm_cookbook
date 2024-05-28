---
layout: recipe
title: Make Points
language: Python
author: Andrew Rohne
libraries-needed: pandas, geopandas, shapely
category: Geopandas
---

This is a simple script that builds points from XY coordinates.

```
gpd.GeoDataFrame(df, geometry=gpd.points_from_xy(df['longitude'], df['latitude']), crs = "EPSG:4326")
```

Note: eps:4326 is wgs84
