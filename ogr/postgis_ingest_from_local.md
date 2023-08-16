
How to ingest a file into postgres + postgis using ogr2ogr.

```
ogr2ogr -f "PostgreSQL" PG:"host=localhost user={USERNAME} password={PASSWORD} dbname=datascience" -t_srs EPSG:4326 -lco GEOMETRY_NAME=geometry -lco SCHEMA=census tlgdb_2022_a_us_substategeo.gdb
```