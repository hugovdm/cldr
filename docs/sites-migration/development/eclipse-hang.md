# Eclipse Hang

Just fyi for those of you running Eclipse on the mac.

Running JVM Monitor, Eclipse hung, so I had to kill it. Afterwords Eclipse would
hang on launch. After a bit of poking on the web, I found that on the Mac, I
could cd to the eclipse directory, eg,

cd /Applications/eclipse

And then run the following, then close and relaunch.

./eclipse -consoleLog -clean -Djava.awt.headless=true

See also: https://bugs.eclipse.org/bugs/show_bug.cgi?id=388170
