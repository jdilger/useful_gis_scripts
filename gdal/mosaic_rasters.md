#### Quick gdal mosaic with compression
very similar to [reproject and compress](./reproject_and_compress.md)


##### general example - mosaic a folder of images
`gdalbuildvrt /vsistdout/ *.tif | gdal_translate -co compress=lzw /vsistdin/ output_file.tif`

##### another example - from a list of files
`gdalbuildvrt -input_file_list my_list.txt /vsistdout/ | gdal_translate -co compress=lzw  /vsistdin/ Richness_10km_AMPHIBIANS_dec2017_EckertIV_threatened_4326.tif`