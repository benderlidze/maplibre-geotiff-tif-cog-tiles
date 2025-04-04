gdal_rasterize -a value -tr 0.01 0.01 -a_nodata 999 -l KEWX_20170220_044018_100 KEWX_20170220_044018_100.geojson KEWX_20170220_044018_101.tiff

gdal_translate -of GTiff -ot Byte -scale KEWX_20170220_044018_101.tiff KE
WX_20170220_044018_100_8bit.tiff

gdal2tiles.py -z 0-12 -w leaflet --processes=4 --tmscompatible KEWX_20170220_044018_100_8bit.tiff output_tiles

https://developmentseed.org/titiler/

gdal_translate -of COG -co COMPRESS=DEFLATE -co BIGTIFF=YES KEWX_20170220_044018_100_8bit.tiff KEWX_20170220_044018_100_cog.tiff

https://labs.geomatico.es/maplibre-cog-protocol/

gdalwarp -t_srs EPSG:3857 KEWX_20170220_044018_101.tiff KEWX_20170220_044018_101_3857.tiff

