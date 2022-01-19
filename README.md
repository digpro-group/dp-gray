Digpro Gray
==========

![screenshot](https://raw.github.com/digpro-group/dp-gray/master/preview.png)

Digpro Gray is meant to be a background map for use when you want to focus on other data rather than the background map.

It is based on OSM Bright (https://github.com/mapbox/osm-bright)

Setup Instructions
------------------

### 1. Download shapefiles

Digpro Gray depends on three shapefiles. You will need to download and extract them before continuing. 

Download them to the `shp` directory in the dp-bright folder. You can do this with `wget` like:

    mkdir dp-gray/shp
    cd dp-gray/shp
    wget https://osmdata.openstreetmap.de/download/simplified-land-polygons-complete-3857.zip
    wget https://osmdata.openstreetmap.de/download/land-polygons-split-3857.zip
    wget http://mapbox-geodata.s3.amazonaws.com/natural-earth-1.4.0/cultural/10m-populated-places-simple.zip

Once downloaded, extract them from their zip files.

    unzip simplified-land-polygons-complete-3857.zip
    unzip land-polygons-split-3857.zip 
    unzip 10m-populated-places-simple.zip

### 2. Run the shapefiles through shapeindex

    shapeindex *.shp */*.shp

### 3. Convert style sheet to XML

    carto dp-gray.mml > dp-gray.xml

### 4. Use in rendering

Update renderd.conf to include something like (update paths for your system).

    [dp-gray]
    URI=/dp-gray/
    TILEDIR=/var/lib/mod_tile
    XML=/home/renderaccount/src/dp-gray/dp-gray/dp-gray.xml
    HOST=localhost
    TILESIZE=256
    MAXZOOM=20

