# Eclipse Setup

OBSOLETE, Need instructions for Git/Jira

[TOC]

We use Eclipse for development and testing of our tools.

Keywords: getting started running tests run

## JDK

*   [JDK
    1.8](http://www.oracle.com/technetwork/java/javase/downloads/index.html) is
    required, so install that first!

## Setup Eclipse and SVN

### (but see alternatives below):

Follow the links below to set up Eclipse as described on the ICU Site. **Make
sure you have “Eclipse for Java EE”.** Set up Subversion also, since you'll need
it soon.

1.  ==<http://site.icu-project.org/setup/java/eclipse-setup-for-java-developers>==
    *   (Stop before the heading "Importing ICU4J")
2.  File->Import, pick SVN, then Projects from SVN.
    Use the URL `http://unicode.org/repos/cldr` for guest access or
    `svn+ssh://unicode.org/repos/cldr` for authenticated access (see [CLDR
    Repository Access](../cldr-repository-access/index.md)) and check out the
    following projects:
    1.  **common** ( as a General project )
    2.  **seed** ( as a General project )
    3.  **test** ( as a General project )
    4.  **java** ( as a Java project - it will be named **cldr-tools** )
    5.  **cldr-apps** ( as a JavaEE project )

### **Alternative 1**

**Markus 2012-oct-25:** I use command-line svn and checkout the whole CLDR tree.
Yoshito says ~~normal~~ developers \[not doing SurveyTool work\] just need to
import one project into Eclipse, from the `<svn.cldr>/tools/java` root. Update
2014-aug-15: You need the `tools/cldr-unittest` project, too.

If there are red x's after importing the project, be sure to define ANT_LIB. If
the ant executable is installed on your machine already, you have the JAR. Just
run "which ant" to find out where the ant executable is (you may have to follow
some symbolic links). Suppose you find the executable at /usr/share/ant/bin/ant,
then the library will be /usr/share/ant/lib/ant.jar. Look below under "Setup
User Libraries" to find out how to tell eclipse where your ant.jar file is.
(Window/Preferences, Java/Build Path/User Libraries, New... name it ANT_LIB, Add
external Jars... find & select /usr/share/ant/lib/ant.jar or wherever it lives
on your system.)

Once you complete this, the red x's should go away and you are ready to run the
unit tests. See test/unit tests below.

You need to set `-DCLDR_DIR=/home/mscherer/svn.cldr/trunk` (change to where you
checked out the CLDR repository) either in the JRE default VM arguments (see
below, although srl does not seem to recommend that \[why?\]) or in each of the
Debug/Run configurations you use for CLDR tests and tools.

### **Alternative 2**

**Mark 2014-jan-28:** I've never been able to get subversive to work, and use
the following instead: [Subeclipse Setup](subeclipse-setup.md).

## Java in Eclipse

*   Make sure to [install the JDK into
    Eclipse](http://stackoverflow.com/a/998643/185799).

## Preferences

Go to Preferences (under **Eclipse** on Mac, under **Window** on others)

TODO: I don't recommend the struck out lines, ever. Especially if you ever run
the SurveyTool. -srl

*   Java>Installed JREs
    *   Pick 1.**7**.0
    *   Edit...
    *   Default VM arguments: (change red to your specific path)
        *   -Dfile.encoding=UTF-8
            -Xmx2000M
            ~~-DSHOW_FILES~~
            ~~-DSHOW~~
            ~~-DCLDR_DIR=${workspace_loc}/cldr/~~
            ~~-DCLDR_ENVIRONMENT=UNITTEST~~
*   Server->Runtime Environment
    *   choose Apache Tomcat v7.0 and click Edit
    *   Add the VM arguments
        *   -Dfile.encoding=UTF-8
            -Xmx2000M

For now, the following formatting settings are suggested. (These settings should
already be in the CLDR tool's eclipse project file), so you shouldn't need to do
anything.

*   General>Workspace: Text File Encoding: UTF-8
*   General>Editors>Text Editors:
    *   Displayed Tab width: 4
    *   Insert spaces for tabs
    *   Show line numbers (optional)
*   Java>Code Style>Formatter:
    *   Edit...
    *   Profile Name: CLDR
    *   Indentation Tab
        *   Tab policy: Spaces Only
        *   Indentation size: 4
        *   Tab size: 4
        *   Align fields in columns
    *   Line Wrapping Tab
        *   Maximum line width: 160
        *   Never Join Lines ✓

## Setup User Libraries

Also, you need to set up user libraries as follows.

*   Java>Build Path>User Libraries
*   Click "New" to add Ant
    *   Specify "ANT_LIB" as the user library name
    *   Get ant libraries from http://ant.apache.org/bindownload.cgi. Extract
        the contents to a local directory YYY/apache-ant-XXX
    *   Click "Add External JARs..." and specify the location of "ant.jar" as
        YYY/apache-ant-XXX/lib/ant.jar

## Test

To make sure that you are up and running, run both of the sets of tests below.
(As you are doing development, you must be sure to fix any failures before
committing your changes.)

In Eclipse, to find any file, type Shift-Command-R.

### Unit tests

*   Goto unittest/TestAll
*   Right-click, Run as... Java Application.
*   Stop it immediately, then open Run>Run
    Configuration>ConsoleCheckCLDR>Arguments (Travis Keep: On my eclipse, I
    found this under ...>Run Configuration>JAVA Application>TestAll>Arguments)
    *   Add -n -u under "Program arguments" section.
    *   Travis Keep: Even if you are not doing SURVEYTOOL work, add
        -DCLDR_DIR=${workspace_loc} in VM arguments section below Program
        arguments section. ${workspace_loc} is the root directory of your
        subversion CLDR working copy.
    *   Travis Keep: Once the tests finish running, you must search for 'FAILED'
        in the output console using Ctrl-F or similar to determine whether or
        not all the tests actually passed. (Isn't this fixed? -srl)
    *   **IF DOING SURVEYTOOL DEVELOPMENT: ADD the following to JVM Arguments**
        -Dfile.encoding=UTF-8
        -Xmx2000M
        -DSHOW_FILES
        -DSHOW
        -DCLDR_DIR=${workspace_loc}/cldr/ (Travis Keep: There is no cldr folder
        under my workspace root)
        -DCLDR_ENVIRONMENT=UNITTEST
*   Hit Run
*   It is a fairly comprehensive test, and takes about 5 minutes to finish.

### Data tests

*   Go to ConsoleCheckCLDR
*   Right-click, Run as... Java Application.
*   Stop it immediately, then open Run>Run Configuration>
    ConsoleCheckCLDR>Arguments
    *   Add -e (Travis Keep: you should have "-n -u -e" under program arguments.
        Since -e sets exhaustiveness to 5 and default exhaustiveness is 0, it
        follows that this procedure covers all the unit tests in the section
        above as well. It seems that one only needs to follow the procedures in
        this "Data tests" section to run all the tests. The section above
        labeled "Unit tests" can be ignored.)
    *   Travis Keep: For the curious, find out more about test program
        parameters by entering -? or -h under "program arguments" and run
        TestAll the same way as in the bullet point above. The documentation on
        the various "program arguments" should appear in the output console.
    *   Travis Keep: Even if you are not doing SURVEYTOOL work, add
        -DCLDR_DIR=${workspace_loc} in VM arguments section below Program
        arguments section. ${workspace_loc} is the root directory of your
        subversion CLDR working copy.
    *   Travis Keep: Once the tests finish running, you must search for 'FAILED'
        in the output console using Ctrl-F or similar to determine whether or
        not all the tests actually passed. (Isn't this fixed? -srl)
    *   **IF DOING SURVEYTOOL DEVELOPMENT: ADD the following to JVM Arguments**
        -Dfile.encoding=UTF-8
        -Xmx2000M
        -DSHOW_FILES
        -DSHOW
        -DCLDR_DIR=${workspace_loc}/cldr/
        -DCLDR_ENVIRONMENT=UNITTEST
*   Hit Run
*   It is a fairly comprehensive test, and takes about 5 minutes to finish.

## Branching

### Create Branch

Right-click on project, select Team>Branch/Tag

Change the "Copy to" URL from .../trunk to something like .../branches/mark

Next

Next (the Create Copy should be HEAD)

Finish

### Switching

Right-click on the project, select Team>Switch to another...

Change the To URL from .../trunk to something like .../branches/mark (or the
reverse)

OK

### Merge a branch back into the trunk:

Switch to branches/X

Merge (reintegrate)

Switch to trunk

Merge (reintegrate)

Commit

## Survey Tool

If you're going to be running the Survey Tool locally, see: [How to build the
Survey Tool under Eclipse](../running-survey-tool/eclipse/index.md).

## Clean Up Source Code

### Organize Imports

You can nicely organize import statements (deleting unused import, sorting
import statements) with simple keyboard operation on Eclipse. When you edit a
Java source code, simply press Ctrl+Shift+O will organize the currently editing
source code. It is encouraged to organize imports whenever you edit a Java
source code.

You can also organize imports in multiple files. To do this, right click on
source code folder(s) in Project Explorer, then select "Source" - "Organize
Imports". In each CLDR release, we make sure import statements are organized in
all Java source files in all projects (cldr-apps / cldr-tools / cldr-unittest).

### Format Source

CLDR Eclipse project files come with its own code formatter setting. To make the
code style consistent across Java source files, it is encouraged to format
source code whenever you edit a new code. To achieve this, you can select a
block of source code, or entire source file (Ctrl+A), followed by Ctrl+Shift+F.

Like organize imports, you can format multiple source files by selecting source
code folder(s) in Project Explorer, select "Source" - "Format". In each CLDR
release, we run through entire CLDR java source files. This operation sometimes
make a lot of modifications if someone write non-standard style Java code.
