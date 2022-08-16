OSM-Garmin
=====

Tools to convert [openstreetmap.org OSM maps] to Garmin maps. Modified to get it building with maven.

Build both mkgmap and splitter with ```mvn clean package```

The original, manuals other versions etc are on 
 https://svn.mkgmap.org.uk/mkgmap/mkgmap. There is a github copy on https://github.com/openstreetmap/mkgmap


See the doc directories, readme and licence files in the modules for more details.

Sample Walkthrough
===============

This example walkthrough shows how to compile an OSM map of your choice.
It is assumed you have java8 sdk, maven, git installed already.
This walkthrough assumes you want to use the "grey" style.
Substitute "grey" with the style of your choice.

1. Download this project
2. cd osm-garmin
3. mvn clean package
4. download a YOURCOUNTRY pbf file from https://download.geofabrik.de to the working directory (root of osm-garmin)
5. mkdir work
6. ``java -jar splitter/target/splitter-412-jar-with-dependencies.jar  --output-dir=work YOURCOUNTRY.osm.pbf``
7. ``java -jar mkgmap/target/mkgmap-4855-jar-with-dependencies.jar --family-id=35 --output-dir=work stylefiles/grey/style/typ/grey.txt work/*.pbf``
8. ``java -jar mkgmap/target/mkgmap-4855-jar-with-dependencies.jar --output-dir=work -c stylefiles/grey/grey_options --style-file=stylefiles/grey/style/grey work/*.pbf stylefiles/grey/style/typ/grey.typ``

In  command 8, the map will be built without sea. To incorporate sea in your final map if needed,
you need to download the latest sea information as well and replace command 8 :

8.  go to https://www.mkgmap.org.uk/download/mkgmap.html and download the latest-sea.zip to your current directory
9.  ``java -jar mkgmap/target/mkgmap-4855-jar-with-dependencies.jar --output-dir=work -c stylefiles/grey/grey_options --style-file=stylefiles/grey/style/grey/ --precomp-sea=sea-latest.zip work/*.pbf stylefiles/grey/style/typ/grey.typ``

 

Now a gmapsupp.img should be in your work dir, ready to be copied to the Garmin.

NOTE1 if you put multiple maps generated this way on your garmin, only one may show up. I think this is due to the name or id of the generated maps to be equal, causing a conflict.

NOTE2 Since 2022, to use the converted maps you seem to need software rev 9.2.9 on the Garmin Edge. Maybe some earlier versions work as well but 7.10 seems not, and most (or all) of the map will be invisible. The only explanation I can think of is that since early 2022 the OSM maps contain some new information. The new information seems correctly translated by this converter, but the older Edge software can not handle it.