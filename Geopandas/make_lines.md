---
layout: recipe
title: Make Lines From Points
language: Python
author: Andrew Rohne
libraries-needed: pandas, geopandas, shapely
category: Geopandas
---

This builds a shapefile of desire lines and will include household fields (and can include person fields).

This specific example is desire lines of home to work locations. "lat" is latitude, "lon" is longitude.

```
import pandas as pd
import geopandas as gpd
from shapely.geometry import Point, LineString

work_dl = persons[~persons['work_lat'].isna()][['hh_id', 'work_lat', 'work_lon']].merge(hh[['home_lat', 'home_lon', 'other', 'fields', 'here']], how = 'left', left_on = 'hh_id', right_index = True)

linest = work_dl.apply(lambda x: LineString([[x['home_lon'], x['home_lat']], [x['work_lon'], x['work_lat']]]), axis = 1)

work_dl = gpd.GeoDataFrame(work_dl, geometry = linest, crs = "EPSG:4326")

work_dl.to_file(os.path.join(QC_GEO_PATH, "work_desline.shp"))
```

Note: eps:4326 is wgs84