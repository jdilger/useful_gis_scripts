You can circumvent downloading a raster but utilizing rasterio's MemoryFile. The memory file will act like a DatasetReader. This is helpful when you need to work with an image but don't need to save it. 

```python
import rasterio as rio
import requests

url = "https://elevation.nationalmap.gov:443/arcgis/services/3DEPElevation/ImageServer/WCSServer?version=1.0.0&request=GetCoverage&service=WCS&Coverage=DEP3Elevation_Slope+Degrees&BBox=-9872152.079313911%2C4732229.52502283%2C-9871906.063239258%2C4732472.130886075&crs=EPSG%3A3857&format=GeoTIFF&width=24&height=24"


_bytes = requests.get(url).content

with rio.MemoryFile(_bytes) as memfile:
    with memfile.open() as src:
        profile = src.profile
        data = src.read(masked=True)

print(data)
print(profile)
```