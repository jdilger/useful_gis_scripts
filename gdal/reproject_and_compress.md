#### Quick gdal reproject with compression
from : https://gis.stackexchange.com/questions/89444/file-size-inflation-normal-with-gdalwarp

##### general example
`gdalwarp -q -t_srs EPSG:32611 -of vrt input_file.tif /vsistdout/ | gdal_translate -co compress=lzw  /vsistdin/ output_file.tif`

##### another example
`gdalwarp -q -t_srs EPSG:4326 -of vrt Richness_10km_AMPHIBIANS_dec2017_EckertIV_threatened.tif /vsistdout/ | gdal_translate -co compress=lzw  /vsistdin/ Richness_10km_AMPHIBIANS_dec2017_EckertIV_threatened_4326.tif`