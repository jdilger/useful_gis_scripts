There are a number of ways to apply and carry no data mask through workflows using rasterio. Below are a couple of examples of doing so..

Using numpy.where()
```python
import rasterio as rio
import numpy as np

input_file = 'some/path/to/a/multi_band.tiff'
multi_img = rio.open(input_file)
bands = [1,2,3,4]
multi_arr = multi_img.read(bands, masked=True)

_mask = np.logical_and.reduce(list(multi_arr.mask))
max_index = np.argmax(multi_arr, axis=0)

max_index_masked = np.where(_mask, multi_img.nodata, max_index)
```


Using numpy.ma (masked array)
```python
import rasterio as rio
import numpy as np

input_file = 'some/path/to/a/multi_band.tiff'
multi_img = rio.open(input_file)
bands = [1,2,3,4]
multi_arr = multi_img.read(bands, masked=True)

_mask = np.logical_and.reduce(list(multi_arr.mask))
max_index = np.argmax(multi_arr, axis=0)

max_index_masked = np.ma.masked_array(max_index, mask=_mask)
```

note: `_mask = np.logical_and.reduce(list(multi_arr.mask))` creates a mask that is the logical `and` of each bands mask. For some cases you might want to use a different logical reducer or mask.