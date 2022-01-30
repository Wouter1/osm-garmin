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

* Download this project
* cd osm-garmin
* mvn clean package
* download a YOURCOUNTRY pbf file from https://download.geofabrik.de to the working directory (root of osm-garmin)
* mkdir work
* java -jar splitter/target/splitter-412-jar-with-dependencies.jar  --output-dir=work YOURCOUNTRY.osm.pbf 
* java -jar mkgmap/target/mkgmap-4855-jar-with-dependencies.jar --family-id=35 --output-dir=work stylefiles/opentopomap/style/typ/opentopomap.tx
* java -jar mkgmap/target/mkgmap-4855-jar-with-dependencies.jar --output-dir=work -c stylefiles/opentopomap/opentopomap_options  --style-file=stylefiles/opentopomap/style/opentopomap --generate-sea=polygon  work/*.pbf work/opentopomap.typ

Now a gmapsupp.img should be in your work dir. 