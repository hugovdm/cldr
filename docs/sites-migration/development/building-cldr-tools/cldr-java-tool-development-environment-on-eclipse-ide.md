# CLDR Java tool development environment on Eclipse IDE

\*\*\* This page is Obsolete Please go to
<http://cldr.unicode.org/development/eclipse-setup>

Eclipse project files for CLDR Java tools are now checked into the CLDR SVN
repository -> http://www.unicode.org/cldr/trac/ticket/2601
This document explains how to set up the CLDR Java tool development environment
with the project files. The instruction in this document is based on Eclipse 3.5
on Windows. If you're using a different version of Eclipse, menu string or
structure might be slightly different.
1. Prerequisites
You need following libraries before setting up the development environment.

*   Java Runtime Environment version 6 or later
*   Apache ant
*   Xalan library
*   ICU4J core jar file and utilities jar file

2. Configuring workspace
When you launch Eclipse, you will be prompted to select a workspace. You can use
existing one, or create a new one.
2.1. Java execution environment
Open the workspace preferences by selecting \[Window\] - \[Preferences\] in the
menu. On the left navigation pain, select "Java" - "Installed JREs" - "Execution
Environment". On the right pain, select "JavaSE-1.6". If you see anything in
"Compatible JREs" list, you're fine. If not, you need to specify the location of
JRE version 6 installed on your environment. To do this, select "Java" -
"Installed JREs" on the left pane, then click "Add" on the right side. Select
"Standard VM" as JRE Type, then specify the installed location to add the JRE.
JRE name is automatically filled in by default. The CLDR Java tools project file
does not depend on JRE name, so you can use any name.
2.2. User libraries
The CLDR Java tools project refers external libraries via "User Libraries".
Because location of these libraries may vary depending on each environment, the
project specify them indirectly. Each developer needs to bind these user
libraries to actual classpath.
The project uses 3 user libraries below -

*   ANT_LIB - Apache ant library (ant.jar)
*   XALAN_LIB - Xalan Java (xalan.jar, xercesImpl.jar, xml-apis.jar)
*   ICU_UTILITIES - ICU4J core and utilities (icu4j.jar, utilities.jar)

To set up these user libraries, select \[Window\] - \[Preferences\] to open the
workspace preferences page. Select "Java" - "Build Path" - "User Libraries" on
the left navigation pane. Then click "New" and specify the library name (e.g.
"ANT_LIB"). Once the library is added in the User Libraries list, select the one
you added and click "Add JARs...". You should specify the target JAR file(s) on
your system. For example, C:\\ant\\lib\\ant.jar for ANT_LIB.
3. Importing CLDR Java tools project
To import the project to your workspace, select \[File\] - \[Import\] fomr the
menu, then select "General" - "Existing Projects into Workspace". In the next
screen, specify the root directory - simply click "Browse" and select the
directory <cldr_root>/tools/java. You should see "cldr-tools" in "Projects"
list. By clicking "Finish", the project should be imported into your workspace.
Note: For now, there are many compiler warnings.

NOTE: I think the above is out of date: people really need to follow the
instructions on the ICU site for developers to get the trunk version of ICU4J:
<http://site.icu-project.org/setup/java/eclipse-setup-for-java-developers>
