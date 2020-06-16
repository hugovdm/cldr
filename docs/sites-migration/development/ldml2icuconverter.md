# LDML2ICUConverter

Caution: This is probably not the page you are looking for. Check here

<http://cldr.unicode.org/development/coding-cldr-tools/newldml2icuconverter>
instead

Whenever you add structure to CLDR, you need to add code to LDML2ICUConverter to
convert to ICU for testing.
We need to flesh out this page more, but here is an example of adding a
conversion:

http://unicode.org/cldr/trac/changeset/4691

See also:

*   ### [Subversion Setup for ICU Developers](/setup/subversion)
*   ### [Eclipse Setup for Java
    Developers](/setup/java/eclipse-setup-for-java-developers)

---

### **Working with LDML2ICUConverter and use it for ICU4C**

A typical setup to do development both in CLDR (LDML2ICUConverter) and ICU4C is:

```none
  

*   root_dir
    *   icu4j_dir
        *   <icu4j_branch_name>
            *   main
    *   <Project1>
        *   cldr
            *   <cldr_branch_name>
                *   common
                *   ...
        *   icu4c
            *   <icu4c_branch_name>
                *   source
    *   <Project2>
        *   ...
        *   ...

```

Here, `<icu4j_branch_name>`, `<cldr_branch_name>`, `<icu4c_branch_name>` are the
branches from which these three projects are checked out. Since icu4j is used
only for running the LDML2ICUConverter, it can be any stable branch or even
trunk. The script below assumes <cldr_branch_name> and <icu4c_branch_name> are
the same, i.e., either they are developed on the trunk or the development
branches are named the same. Some tweaking of the scripts are needed if they are
different.
The rest of this document assumes that the commands are run from `root_dir`.

#### Checking out

Checkout can be done as follows:

1.  **ICU4J:** `mkdir icu4j_dir ; cd icu4j_dir ; `
    1.  **Trunk:** `svn co
        svn+ssh://source.icu-project.org/repos/icu/icu4j/trunk`
    2.  **Branch:** `svn co
        svn+ssh://source.icu-project.org/repos/icu/icu4j/branches/<icu4j_branch_name>`
2.  **<Project>:** `mkdir <Project> ;`
    1.  **CLDR:** `mkdir <Project>/cldr ; cd <Project1>/cldr ; `
        1.  Trunk: `svn co svn+ssh://unicode.org/repos/cldr/trunk`
        2.  Branch: `svn co
            svn+ssh://unicode.org/repos/cldr/branches/<branch_name>`
    2.  **ICU4C:** `mkdir <Project>/icu4c ; cd <Project1>/icu4c ; `
        1.  Trunk: `svn co svn+ssh://source.icu-project.org/repos/icu/icu/trunk`
        2.  Branch: `svn co
            svn+ssh://source.icu-project.org/repos/icu/icu/branches/<branch_name>`

#### Building LDML tools

To build LDML tools, use the following script (`build_ldml.sh`) .

*   Uasge: `build_ldml.sh [-c] [-b <branch_name>] [-j <icu4j_branch_name>]
    <project>`.
    *   `-c `causes clean build, `-b` allows to provide a branch name for cldr
        and icu4c ('trunk' if absent) , and `-j` allows to provide a branch name
        for icu4j ('trunk' if absent).
    *   The mandatory `<project>` parameter specifies from which subdirectory
        the programs and data should be used.
    *   There is hardly any need for a clean build, because the dependencies are
        pretty much OK; but the whole build does not take much much time, so it
        doesn't hurt to do a clean build every time.

```none
#!/bin/bash
BRANCH_NAME='trunk'
ICU4J_BRANCH_NAME='trunk'
CLEAN_FLAG=
while getopts 'b:j:c' BRANCH_OPTION
do
  case "$BRANCH_OPTION" in
    b) BRANCH_NAME="$OPTARG" ;;
    j) ICU4J_BRANCH_NAME="$OPTARG" ;;
    c) CLEAN_FLAG=1 ;;
    *) printf "Usage: %s [-b <branch_name>] [-j <icu4j_branch_name>] <project>\n" $(basename 0) >&2
      exit -1 ;;
  esac
done
shift $(($OPTIND-1))
PROJECT=$1
while true; do
  if [ -z "$PROJECT" ]; then
    echo Project is missing.
    break
  fi
  CURR_DIR=`pwd`
  export ICU4JDIR=$CURR_DIR/icu4j-trunk/$ICU4J_BRANCH_NAME
  if [ ! -d "$ICU4JDIR" ]; then
    echo \$ICU4JDIR=$ICU4JDIR is not a directory.
    break
  fi
  export CLDR_DIR=$CURR_DIR/$PROJECT/cldr/$BRANCH_NAME
  if [ ! -d "$CLDR_DIR" ]; then
    echo \$CLDR_DIR=$CLDR_DIR is not a directory.
    break
  fi
  echo "\$ICU4JDIR = $ICU4JDIR"
  echo "\$CLDR_DIR = $CLDR_DIR"
  export ICU4J_JAR=$ICU4JDIR/icu4j.jar
  echo "\$ICU4J_JAR = $ICU4J_JAR"
  if [ ! -f $ICU4J_JAR ]; then
    echo \$ICU4J_JAR does not exist.
    break
  fi
  export UTILITIES_JAR=$ICU4JDIR/out/cldr_util/lib/utilities.jar
  echo "\$UTILITIES_JAR = $UTILITIES_JAR"
  if [ ! -f $UTILITIES_JAR ]; then
    echo \$UTILITIES_JAR does not exist.
    break
  fi
  ICU4J_CLASSES_1="$ICU4JDIR/main/classes/core/out/bin"
  ICU4J_CLASSES_2="$ICU4JDIR/out/cldr_util/bin"
  export ICU4J_CLASSES="$ICU4J_CLASSES_1:$ICU4J_CLASSES_1"
  echo "\$ICU4J_CLASSES = $ICU4J_CLASSES"
  if [ ! -d $ICU4J_CLASSES_1 ]; then
    echo $ICU4J_CLASSES_1 does not exist.
    break
  fi
  if [ ! -d $ICU4J_CLASSES_2 ]; then
    echo $ICU4J_CLASSES_2 does not exist.
    break
  fi
  export XML_APIS_JAR=/usr/share/java/xalan2.jar
  echo "\$XML_APIS_JAR = $XML_APIS_JAR"
  if [ ! -f $XML_APIS_JAR ]; then
    echo \$XML_APIS_JAR does not exist.
    break
  fi
  export CLDR_CLASSES="$CLDR_DIR/tools/java/classes:$CLDR_DIR/tools/java"
  cd $CLDR_DIR/tools/java
  if [ "$CLEAN_FLAG" ]; then
    ant clean
  fi
  ant all
  ant jar
  ant icu
  break
done
```

#### Generating ICU4C locale data files from CLDR data files

To generate ICU4C .txt files from the CLDR .xml files, use the following script
(`gen_icu4c_txt.sh`).

*   Usage: `gen_icu4c_txt.sh [-c] [-b <branch_name>] [-j <icu4j_branch_name>]
    <Project>`.
*   `-c `causes clean build, `-b` allows to provide a branch name for cldr and
    icu4c ('trunk' if absent) , and `-j` allows to provide a branch name for
    icu4j ('trunk' if absent).
*   The mandatory `<project>` parameter specifies from which subdirectory the
    programs and data should be used.
*   Use the` -c` flag when you change CLDR .xml files, because there is no
    dependency between these two sets of files. If you want to generate only one
    file, delete the file from the ICU4C source tree:
    `<Project>/icu4c/<branch_name>/source/data/<module>/<locale>.txt`, and then
    invoke `gen_icu4c_txt.sh` without the` -c` flag.

```none
#!/bin/bash
BRANCH_NAME='trunk'
ICU4J_BRANCH_NAME='trunk'
CLEAN_FLAG=
while getopts 'b:j:c' BRANCH_OPTION
do
  case "$BRANCH_OPTION" in
    b) BRANCH_NAME="$OPTARG" ;;
    j) ICU4J_BRANCH_NAME="$OPTARG" ;;
    c) CLEAN_FLAG=1 ;;
    *) printf "Usage: %s [-b <branch_name>] [-j <icu4j_branch_name>] [-c] <project>\n" $(basename 0) >&2
      exit -1 ;;
  esac
done
shift $(($OPTIND-1))
PROJECT=$1
while true; do
  if [ -z "$PROJECT" ]; then
    echo Project is missing.
    break
  fi
  CURR_DIR=`pwd`
  export ICU4JDIR=$CURR_DIR/icu4j-trunk/$ICU4J_BRANCH_NAME
  echo "\$ICU4JDIR = $ICU4JDIR"
  if [ ! -d "$ICU4JDIR" ]; then
    echo \$ICU4JDIR=$ICU4JDIR is not a directory.
    break
  fi
  export CLDR_DIR=$CURR_DIR/$PROJECT/cldr/$BRANCH_NAME
  echo "\$CLDR_DIR = $CLDR_DIR"
  if [ ! -d "$CLDR_DIR" ]; then
    echo \$CLDR_DIR=$CLDR_DIR is not a directory.
    break
  fi
  export ICU4J_JAR=$ICU4JDIR/icu4j.jar
  echo "\$ICU4J_JAR = $ICU4J_JAR"
  if [ ! -f $ICU4J_JAR ]; then
    echo \$ICU4J_JAR does not exist.
    break
  fi
  export UTILITIES_JAR=$ICU4JDIR/out/cldr_util/lib/utilities.jar
  echo "\$UTILITIES_JAR = $UTILITIES_JAR"
  if [ ! -f $UTILITIES_JAR ]; then
    echo \$UTILITIES_JAR does not exist.
    break
  fi
  ICU4J_CLASSES_1="$ICU4JDIR/main/classes/core/out/bin"
  ICU4J_CLASSES_2="$ICU4JDIR/out/cldr_util/bin"
  export ICU4J_CLASSES="$ICU4J_CLASSES_1:$ICU4J_CLASSES_2"
  echo "\$ICU4J_CLASSES = $ICU4J_CLASSES"
  if [ ! -d $ICU4J_CLASSES_1 ]; then
    echo $ICU4J_CLASSES_1 does not exist.
    break
  fi
  if [ ! -d $ICU4J_CLASSES_2 ]; then
    echo $ICU4J_CLASSES_2 does not exist.
    break
  fi
  export XML_APIS_JAR=/usr/share/java/xalan2.jar
  echo "\$XML_APIS_JAR = $XML_APIS_JAR"
  if [ ! -f $XML_APIS_JAR ]; then
    echo \$XML_APIS_JAR does not exist.
    break
  fi
  CLDR_CLASSES_1="$CLDR_DIR/tools/java/classes"
  CLDR_CLASSES_2="$CLDR_DIR/tools/java"
  export CLDR_CLASSES="$CLDR_CLASSES_1:$CLDR_CLASSES_2"
  echo "\$CLDR_CLASSES = $CLDR_CLASSES"
  if [ ! -d $CLDR_CLASSES_1 ]; then
    echo $CLDR_CLASSES_1 does not exist.
    break
  fi
  if [ ! -d $CLDR_CLASSES_2 ]; then
    echo $CLDR_CLASSES_2 does not exist.
    break
  fi
  export ICU4C_DIR=$CURR_DIR/$PROJECT/icu4c/$BRANCH_NAME
  echo "\$ICU4C_DIR = $ICU4C_DIR"
  if [ ! -d $ICU4C_DIR ]; then
    echo \$ICU4C_DIR is not a directory.
    break
  fi
  cd $ICU4C_DIR/source/data
  if [ "$CLEAN_FLAG" ]; then
    ant clean
  fi
  ant all
  break
done
```

#### (Configuring and ) Building ICU4C

To build ICU4C, use the following script (`build_icu4c.sh`).

*   `build_icu4c.sh [-c] [-t] [-b <branch_name>] <project>`Usage:
*   `-c `causes clean build, `-b` allows to provide a branch name for icu4c
    ('trunk' if absent), and -t runs all the tests also.
*   The mandatory `<project>` parameter specifies from which subdirectory the
    programs and data should be used.
*   It creates (if it doesn't already exist) a directory `dev` parallel to the
    source directory and does an out of source build.
*   It is safe to use the `-c` flag, because the dependencies are not that
    dependable. An alternative is to delete the .res files to rebuild from
    `<Project>/icu4c/<branch_name>/dev/data/out/build/icudt${VERSION}${PLATFORM}/<module>/<locale>.res`
    and then run `build_icu4c.sh` without the -c flag. This will save a lot of
    time.
*   If you get a message that the workspace should be reconfigured and rebuilt,
    do `rm -rf <Project>/icu4c/<branch_name>/dev `and invoke the script.

```none
#!/bin/bash
BRANCH_NAME='trunk'
CLEAN_FLAG=
TEST_FLAG=
while getopts 'b:j:ct' BRANCH_OPTION
do
  case "$BRANCH_OPTION" in
    b) BRANCH_NAME="$OPTARG" ;;
    c) CLEAN_FLAG=1 ;;
    t) TEST_FLAG=1 ;;
    *) printf "Usage: %s [-b <branch_name>] [-c] [-t]  <project>\n" $(basename 0) >&2
      exit -1 ;;
  esac
done
shift $(($OPTIND-1))
PROJECT=$1
while true; do
  if [ -z "$PROJECT" ]; then
    echo Project is missing.
    break
  fi
  CURR_DIR=`pwd`
  DEV_DIR=$CURR_DIR/$PROJECT/icu4c/$BRANCH_NAME/dev
  if [ ! -d $DEV_DIR ]; then
    echo Creating development directory...
    mkdir $DEV_DIR
    cd $DEV_DIR
    echo Configuring build environment....
    ../source/runConfigureICU Linux
  fi
  cd $DEV_DIR
  if [ "$CLEAN_FLAG" ]; then
    echo Cleaning...
    make clean
  fi
  echo Building...
  make
  if [ "$TEST_FLAG" ]; then
    echo Testing...
    make check
  fi
  break
done
```

#### Running LDML2ICUConverter standalone

Warning: LDML2ICUConverter is partly deprecated.
[NewLdml2IcuConverter](coding-cldr-tools/newldml2icuconverter.md) now handles
conversion of locale, supplemental and bcp47 data. The script here should be
used for those types of data anymore.

With the setup given above and a default working directory `root_dir/tmp`, the
following script (`run_ldml2icuconverter.sh`) can be used.

*   Usage: `run_ldml2icuconverter.sh [-d <output_dir> ] [-b <branch_name>] -l
    <locale> -m module <project>`
*   The mandatory `-l `switch should provide the locale. The script will read
    the `<locale>.xml` from the input directory and write `<locale>.txt` in the
    output directory.
*   The mandatory `-m` switch should provide the module (coll, rbnf, main etc.).
*   The mandatory `<project>` parameter specifies from which subdirectory the
    programs and data should be used.

```none
#!/bin/bash
BRANCH_NAME='trunk'
ICU4J_BRANCH_NAME='trunk'
OUT_DIR=
MODULE=
LOCALE=
while getopts 'b:d:j:l:m:' BRANCH_OPTION
do
  case "$BRANCH_OPTION" in
    b) BRANCH_NAME="$OPTARG" ;;
    d) OUT_DIR="$OPTARG" ;;
    j) ICU4J_BRANCH_NAME="$OPTARG" ;;
    l) LOCALE="$OPTARG" ;;
    m) MODULE="$OPTARG" ;;
    *) printf "Usage: %s [-b <branch_name>] [-j <icu4j_branch_name>] <project>\n" $(basename 0) >&2
      exit -1 ;;
  esac
done
shift $(($OPTIND-1))
PROJECT=$1
while true; do
  if [ -z "$PROJECT" ]; then
    echo Project is missing.
    break
  fi
  echo "\$MODULE = $MODULE"
  if [ -z "$MODULE" ]; then
    echo Module is missing.  Use the -m switch to specify the locale.
    break
  fi
  echo "\$LOCALE = $LOCALE"
  if [ -z "$LOCALE" ]; then
    echo Locale is missing.  Use the -l switch to specify the locale.
    break
  fi
  CURR_DIR=`pwd`
  if [ -z "$OUT_DIR" ]; then
    OUT_DIR=$CURR_DIR/tmp
  fi
  if [ ! -d "$OUT_DIR" ]; then
    echo "$OUT_DIR should be present."
    break
  fi
  export ICU4JDIR=$CURR_DIR/icu4j-trunk/$ICU4J_BRANCH_NAME
  if [ ! -d "$ICU4JDIR" ]; then
    echo \$ICU4JDIR=$ICU4JDIR is not a directory.
    break
  fi
  export CLDR_DIR=$CURR_DIR/$PROJECT/cldr/$BRANCH_NAME
  if [ ! -d "$CLDR_DIR" ]; then
    echo \$CLDR_DIR=$CLDR_DIR is not a directory.
    break
  fi
  echo "\$ICU4JDIR = $ICU4JDIR"
  echo "\$CLDR_DIR = $CLDR_DIR"
  export ICU4J_JAR=$ICU4JDIR/icu4j.jar
  echo "\$ICU4J_JAR = $ICU4J_JAR"
  if [ ! -f $ICU4J_JAR ]; then
    echo \$ICU4J_JAR does not exist.
    break
  fi
  export UTILITIES_JAR=$ICU4JDIR/out/cldr_util/lib/utilities.jar
  echo "\$UTILITIES_JAR = $UTILITIES_JAR"
  if [ ! -f $UTILITIES_JAR ]; then
    echo \$UTILITIES_JAR does not exist.
    break
  fi
  ICU4J_CLASSES_1="$ICU4JDIR/main/classes/core/out/bin"
  ICU4J_CLASSES_2="$ICU4JDIR/out/cldr_util/bin"
  export ICU4J_CLASSES="$ICU4J_CLASSES_1:$ICU4J_CLASSES_1"
  echo "\$ICU4J_CLASSES = $ICU4J_CLASSES"
  if [ ! -d $ICU4J_CLASSES_1 ]; then
    echo $ICU4J_CLASSES_1 does not exist.
    break
  fi
  if [ ! -d $ICU4J_CLASSES_2 ]; then
    echo $ICU4J_CLASSES_2 does not exist.
    break
  fi
  export XML_APIS_JAR=/usr/share/java/xalan2.jar
  echo "\$XML_APIS_JAR = $XML_APIS_JAR"
  if [ ! -f $XML_APIS_JAR ]; then
    echo \$XML_APIS_JAR does not exist.
    break
  fi
  export CLDR_CLASSES="$CLDR_DIR/tools/java/classes:$CLDR_DIR/tools/java"
  INPUT_DIR=$CLDR_DIR/common/$MODULE
  if [ ! -d "$INPUT_DIR" ]; then
    echo
    echo "\$INPUT_DIR=$INPUT_DIR is not a directory.  Probably you have an invalid module \"$MODULE\"."
    echo "Valid modules are bcp47 collation main rbnf segments supplemental transforms."
    break
  fi
  java \
    -cp "$UTILITIES_JAR:$ICU4J_JAR:$XML_APIS_JAR:$CLDR_CLASSES:/usr/share/java/xml-apis.jar:/usr/share/java/xercesImpl.jar:/usr/share/java/ant.jar" \
    -Dfile.encoding=UTF-8 -Xmx700M -DSHOW_FILES -DSHOW -DCLDR_DIR=$CLDR_DIR \
    org.unicode.cldr.icu.LDML2ICUConverter \
    -s $INPUT_DIR \
    -m $CLDR_DIR/common/supplemental \
    -d $OUT_DIR \
    $LOCALE.xml
  break
done
```

#### Comparing generated files and data sizes

The following Python program (`comp_dirs.py`) can be used to compare the file
sizes in two directories.

*   Usage: comp_dirs.py <dir1> <dir2>
*   Gives details of files existing in one directory but not the other. Also,
    gives useful statistics.

```none
#!/usr/bin/python
import filecmp
import os
import os.path
import sys
class CmpDirs:
  def __init__(self, dir1, dir2):
    self.commonFiles = set()
    self.changedWithSameSizeFiles = set()
    self.shrunkFiles = {}
    self.expandedFiles = {}
    self.dir1 = dir1
    self.dir2 = dir2
    self.totalSize1 = 0L
    self.totalSize2 = 0L
    self.totalChanged1 = 0L
    self.totalChanged2 = 0L
  def compareFiles(self, filename):
    file1 = "%s/%s" % (self.dir1, filename)
    file2 = "%s/%s" % (self.dir2, filename)
    size1 = os.path.getsize(file1)
    size2 = os.path.getsize(file2)
    self.totalSize1 += size1
    self.totalSize2 += size2
    if size1 == size2:
      if not filecmp.cmp(file1, file2):
        self.changedWithSameSizeFiles.add(filename)
    else:
      self.totalChanged1 += size1
      self.totalChanged2 += size2
      sizes = [size1, size2]
      if size1 > size2:
        self.shrunkFiles[filename] = sizes
      else:
        self.expandedFiles[filename] = sizes
  def compareDirectories(self):
    files1 = set(os.listdir(self.dir1))
    files2 = set(os.listdir(self.dir2))
    if (files1 != files2):
      print "Directories have different contents"
      diff1 = files1 - files2
      if diff1:
        print "The following files exist in %s but not in %s" % (self.dir1, self.dir2)
        print "  " + "\n  ".join(diff1)
      diff2 = files2 - files1
      if diff2:
        print "The following files exist in %s but not in %s" % (self.dir2, self.dir1)
        print "  " + "\n  ".join(diff2)
    self.commonFiles = files1 & files2
    for f in self.commonFiles:
      self.compareFiles(f)
  def report(self):
    headerFormat = "%-40s = %12ld"
    headerFormatWithPercentage = "%-40s = %12ld (%10.2f%%)"
    print "COMPARISON OF DIRECTORIES %s and %s" % (self.dir1, self.dir2)
    print
    print headerFormat % ("Number of files", len(self.commonFiles))
    print headerFormat % ("Number of shrunk files", len(self.shrunkFiles))
    print headerFormat % ("Number of expanded files", len(self.expandedFiles))
    print headerFormat % ("Total size (original)", self.totalSize1)
    if self.totalSize1 == 0L:
      print "No change in total size."
    else:
      print headerFormatWithPercentage % ("Total size (final)", self.totalSize2,
                                          self.totalSize2 * 100.0 / self.totalSize1)
    print headerFormat % ("Total size of changed files (original)", self.totalChanged1)
    if self.totalChanged1 == 0L:
      print "No files changed."
    else:
      print headerFormatWithPercentage % ("Total size of changed files (final)", self.totalChanged2,
                                          self.totalChanged2 * 100.0 / self.totalChanged1)
    print
    headingLines = "-" * 55
    heading = "%-20s%12s%12s%11s" % ("File", "Old size", "New size", "Percentage")
    if len(self.shrunkFiles) > 0:
      print "\nSHRUNK FILES:"
      print headingLines
      print heading
      print headingLines
      for f in sorted(self.shrunkFiles.keys()):
        sizes = self.shrunkFiles[f]
        print "%-20s%12ld%12ld%8.2f %%" % (f, sizes[0], sizes[1], sizes[1] * 100.0 / sizes[0])
    if len(self.expandedFiles) > 0:
      print "\nEXPANDED FILES:"
      print headingLines
      print heading
      print headingLines
      for f in sorted(self.expandedFiles.keys()):
        sizes = self.expandedFiles[f]
        print "%-20s%12ld%12ld%8.2f %%" % (f, sizes[0], sizes[1], sizes[1] * 100.0 / sizes[0])
    print headingLines
if __name__ == "__main__":
  if len(sys.argv) < 3:
    print "Usage: comp_dirs.py <old_dir> <new_dir>"
    sys.exit(1)
  cd = CmpDirs(sys.argv[1], sys.argv[2])
  cd.compareDirectories()
  cd.report()
```
