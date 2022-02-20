The available styles
====================

There are a number of styles in here.

* grey is opentopomap style but modified to have green (forest) and water almost grey, from https://github.com/der-stefan/OpenTopoMap/blob/master/garmin
The grey style enables the planned route lines and turn indications to really stand out. This is useful when driving, as your main interest is on where to go.

* Dark is also derived from the opentopomap style, but all colors have been made much darker. The original idea here was that this makes it easy to see the planned route lines to stand out. This works great inside a dimmer environment (eg, when it's dark). But it does not work so great in bright sunlight, where this style makes the screen just look black.

Changing a type 
====

After editing a typ.txt file you need to compile it with
 ``java -cp "mkgmap.jar:lib/*.jar" uk.me.parabola.mkgmap.main.TypCompiler INPUT_FILE OUTPUT_FILE``

eg
``java -cp mkgmap/target/mkgmap-4855-jar-with-dependencies.jar uk.me.parabola.mkgmap.main.TypCompiler stylefiles/grey/style/typ/grey.txt  stylefiles/grey/style/typ/grey.typ``
