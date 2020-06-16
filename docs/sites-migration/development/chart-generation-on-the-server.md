# Chart generation on the server

Note: Obsolete. There isn't any daily chart generation. -srl

Example of adding generation of a "chart" to the server's daily update script.
The update scripts live in ~jakarta, owned by jakarta user. You will need to
login as that user or "su" to the jakarta user to continue.
0. Run the ~jakarta/.cldrrc script to make sure your CVS root is properly set.
1. go into ~jakarta/bin and symlink CLDRWrapper to \[Your New Chart Name\] by
invoking "ln -s CLDRWrapper Your_new_thing".
2. If the tool wasn't in the **org.unicode.cldr.tool** package, you would have
to edit CLDRWrapper just below the line that says "no need to change below this
line" to reference that particular tool. You may be able to skip this step if
your chart generator is already included. Ask Steven for assistance if you have
to edit that.
3. cd to directory ~jakarta/stbk and edit update-supplemental.sh:
1. add a new section to execute the ~/bin/\[Your New Chart Name\] script
2. update the cvs update / cvs commit section to commit the right stuff.
There are several scripts already being run, so you can copy the setup of shell
variables, then copy the last few lines for the cvs update and commit.

### The chart programs are:

Run Program: tool/ShowLanguages
Parameters:
\[changing /Users/markdavis/... to whatever is appropriate on the machine\]
-Dfile.encoding=UTF-8
-Xmx700M
-DSHOW_FILES
-DSHOW

-DCLDR_DIR=/Users/markdavis/Documents/workspace/cldr/src/
-DCLDR_MAIN=/Users/markdavis/Documents/workspace/cldr/src/incoming/vetted/main/
Then have it check in diff/supplemental/.\* into CVS.
===
To generate the by_type charts, could you please add:
Run Program: GenerateSidewaysView
Parameters: \[same as above\]
Then have it check in /diff/by_type/.\* into CVS
===
To generate the summary charts, could you please add:
Run Program: tool/ShowData
Parameters: \[same as above\]
Then have it check in /diff/summary/.\* into CVS

===

GenerateTransformCharts
