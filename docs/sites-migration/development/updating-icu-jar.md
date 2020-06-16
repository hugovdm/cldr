# Updating ICU jar

The short instructions are:

On the ICU4J side, there's an ant target called "releaseCLDR". So you run that
from your current trunk ICU4J, and it will create 2~~4~~ jar files in
<ICU4J>/release_cldr/

*   icu4j.jar
*   icu4j-src.jar
*   ~~utilities.jar~~
*   ~~utilities-src.jar .~~

Take these 2~~4~~ jar files, copy them over to <CLDR>/tools/java/libs.

In Eclipse

*   Find icu4j/build.xml
*   Right-click, Run As..., External Tools Configuration
*   Pick Targets tab
*   Check 'releaseCLDR', about 1/2 way down (and uncheck anything else)
*   Run
*   Open icu4j/release_cldr/
*   Select the 2~~4~~ files, copy.
*   Open cldr/tools/java/libs
*   Paste

Check them into SVN...
