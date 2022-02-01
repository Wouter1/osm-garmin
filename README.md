OSM-Garmin
=====

Tools to convert [openstreetmap.org OSM maps] to Garmin maps. Modified to get it building with maven.

Build both mkgmap and splitter with ```mvn clean package```

The original, manuals other versions etc are on 
 https://svn.mkgmap.org.uk/mkgmap/mkgmap. There is a github copy on https://github.com/openstreetmap/mkgmap


See the doc directories, readme and licence files in the modules for more details.

Sample Walkthrough
===============
NOTICE this is not yet tested

This example walkthrough shows how to compile an OSM map of your choice.
It is assumed you have java8 sdk, maven, git installed already.
This walkthrough assumes you want to use the opentopomap style.
Substitute opentopomap with the style of your choice.

1 Download this project
2 cd osm-garmin
3 mvn clean package
4 download a YOURCOUNTRY pbf file from https://download.geofabrik.de to the working directory (root of osm-garmin)
5 mkdir work
6 java -jar splitter/target/splitter-412-jar-with-dependencies.jar  --output-dir=work YOURCOUNTRY.osm.pbf 
7 java -jar mkgmap/target/mkgmap-4855-jar-with-dependencies.jar --family-id=35 --output-dir=work stylefiles/opentopomap/style/typ/opentopomap.txt work/*.pbf
8 java -jar mkgmap/target/mkgmap-4855-jar-with-dependencies.jar --output-dir=work -c stylefiles/opentopomap/opentopomap_options  --style-file=stylefiles/opentopomap/style/opentopomap work/*.pbf work/opentopomap.typ work/*.pbf

In  command 8, the map will be built without sea. To incorporate sea in your final map,
you need to download the latest sea information as well and replace command 8 :
8  go to https://www.mkgmap.org.uk/download/mkgmap.html and download the latest-sea.zip to your current directory
10 java -jar mkgmap/target/mkgmap-4855-jar-with-dependencies.jar --output-dir=work -c stylefiles/opentopomap/opentopomap_options  --style-file=stylefiles/opentopomap/style/opentopomap --precomp-sea=sea-latest.zip  work/*.pbf work/opentopomap.typ work/*.pbf

 

Now a gmapsupp.img should be in your work dir. 