
opentopomap style but modified to have green (forest) and water almost grey, from https://github.com/der-stefan/OpenTopoMap/blob/master/garmin


After editing the typ.txt file you need to compile it with
 ``java -cp "mkgmap.jar:lib/*.jar" uk.me.parabola.mkgmap.main.TypCompiler INPUT_FILE OUTPUT_FILE``

eg
``java -cp mkgmap/target/mkgmap-4855-jar-with-dependencies.jar uk.me.parabola.mkgmap.main.TypCompiler stylefiles/grey/style/typ/grey.txt  stylefiles/grey/style/typ/grey.typ``