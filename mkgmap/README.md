MkgMap
=====

This is a modified mkgmap, to get it building with maven.

For the original, manuals other versions etc please refer to 	
https://svn.mkgmap.org.uk/mkgmap/mkgmap. There is a github copy on https://github.com/openstreetmap/mkgmap

Documentation is in the doc folder and also online https://www.mkgmap.org.uk/doc/options. General info on https://www.mkgmap.org.uk/doc/index.html. 


A defunct but still very useful walkthrough on how to build a map is on 
https://github.com/der-stefan/OpenTopoMap/tree/master/garmin


Building
======
You need to install OSM-splitter version 412 before this compiles. Check https://github.com/Wouter1/OSM-splitter
After that you can use the standard ```mvn clean install``` to build mkgmap (including running all tests)

PrecompSeaGenerator
=======
This code includes the PrecompSeaGenerator.


Use
===
