# NewLdml2IcuConverter

## Introduction

The new CLDR to ICU converter is driven by a series of regexes for LDML XPaths,
each mapping to its own set of processing instructions. The overall goal of the
converter is to require little or no code to be written when adding new values
to be processed. The addition of regexes should also be straightforward, i.e.
the user should not have to read code to add a new regex.
If any code does need to be added to accommodate a new processing instruction in
the regex file, it must be generalised such that the new instruction could be
added to any line in the regex file if needed. Hacks in code should be labelled
as such, along with a comment about when the hack can be removed.

## Running NewLdml2IcuConverter

For a full list of options, run org.unicode.cldr.icu.NewLdml2IcuConverter
--help. NewLdml2IcuConverter is also run as part of ICU4C's build process.

## Running NewLdml2IcuConverter via Eclipse while changing ldml2icu_locale.txt (instant gratification)

If you are changing ldml2icu_locale.txt or similar file, it may be useful to
test your changes by quickly running NewLdml2IcuConverter in eclipse.

1.  open NewLdml2IcuConverter.java using Ctrl+Shift+R.
2.  With NewLdml2IcuConverter.java visible do Run -> Run As -> Java application.
    This will fail.
3.  Run -> Run Configurations -> NewLdml2IcuConverter -> Arguments
    Here you specify Program Arguments and VM arguments for eclipse to run
    NewLdml2IcuConverter. Here are mine.
    Program arguments:
    -s ${workspace_loc}/cldr/common/main **// when generating supplemental
    files, use ${workspace_loc}/cldr/common/supplemental**
    -m ${workspace_loc}/cldr/common/supplemental
    -d ${workspace_loc}/icu/trunk/src/source/data/locales
    -t locales
    en // list of space-separated locales, or a regex; .\* for all files
    VM arguments:
    -DCLDR_DIR=/home/rocketman/svn.cldr/trunk6
    Note that my CLDR subversion working copy is located at
    /home/rocketman/svn.cldr/trunk6 and my ICU subversion working copy is
    located at /home/rocketman/svn.icu/trunk/src
    When I run NewLdml2IcuConverter in this way, it will write out a new
    "en.txt" file to my ICU subversion working copy clobbering my old one (note
    the "en" at the end of my program arguments). Then I can run svn diff from
    my ICU working copy to see what the work I did will actually change.
4.  Hit "apply" and "run" near bottom of dialog box
5.  After a few seconds, NewLdml2ICUConverter will emit en.txt. If you want to
    test with another locale, say "fr", just change the "en" to "fr" at the end
    of my Program arguments.

### Filtering

Here are examples of filtering to just given files:

-s ${workspace_loc}/cldr/common/segments

-d "/Users/markdavis/Google
Drive/Backup-2012-10-09/Documents/indigo/Generated/cldr/icu/brkitr"

-p /Users/markdavis/workspace/icu4c/source/data/xml/brkitr

-t brkitr

-g /Users/markdavis/workspace/icu4c/source/data/brkitr/brkfiles.mk

### **Test CLDR and ICU**

When finished, be sure to [test
CLDR](http://cldr.unicode.org/development/eclipse-setup#TOC-Data-tests). Finally
test your changes with ICU by first generating "en" and "root" in your ICU
working copy, see #5 in preceding section. Then test ICU (TODO: Add link to page
describing how to test ICU). If tests fail, try reverting any changes that are
not caused directly by your work. If ICU tests still fail, see troubleshooting
below.

**ICU Test troubleshooting**

*   /tsutil/cldrtest/TestLocaleStructure fails - You may see a message that
    looks like "Can't open a resource with key "NoonMarker" in "gregorian" from
    root for locale "en" If this happens, be sure to edit
    source/test/testdata/structLocale.txt in your ICU working copy and add
    placeholders for the data you are adding.

## Converting new data in an existing XML file

This section is for new data that has been added into common/main or existing
files in common/supplemental. For an example of an actual change, see changeset
[8157](http://unicode.org/cldr/trac/changeset/8157).

1.  Edit the regex file to include the new data (ldml2icu_locale.txt or
    ldml2icu_supplemental.txt). For a full description of the syntax used in the
    regex files, see ldml2icu_readme.txt.
2.  If the new data needs to be output into a different directory than ICU's
    data/locale or data/misc, edit ldml2icu_dir_mapping.txt to move the new
    data's rbPaths to the right directory.
3.  Run NewLdml2IcuConverter to verify the output.

## Converting a new type of XML file

For an example of an actual change, see changeset
[7432](http://unicode.org/cldr/trac/changeset/7432).

1.  Add the filename to the NewLdml2IcuConverter.Type enum. When running
    NewLdml2IcuConverter, the file will be converted by setting the parameter
    `--type=<filename>`.
2.  Perform file conversion by doing one of the following:
    1.  Add instructions for parsing the input file to the regex file of the
        relevant mapper. See `ldml2icu_readme.txt` for detailed instructions.
    2.  If the file requires a mapping that can’t be supported by the regex
        files, follow the example of PluralsMapper and create a new mapper that
        does the conversion through code instead.
3.  Run NewLdml2IcuConverter to verify the output.
4.  Add a corresponding build rule for the new file to ICU's
    [build.xml](http://source.icu-project.org/repos/icu/icu/trunk/source/data/build.xml).
5.  If the given rb path should always present its values as an array, then you
    must modify IcuTextWriter.java

## Exclusions

TestLdml2ICU is where the exclusions are listed. In some cases, paths are
excluded because the code hasn't been added to convert them yet, but those
should all be fixed before the release is done.

## List of files

**FilenameDescription** NewLdml2IcuConverter.java The executing file. Works with
Ant. LdmlMapper.java The superclass of all mappers that use regex files for data
mapping LocaleMapper.java Mapper for locale data SupplementalMapper.java Mapper
for supplemental data PluralsMapper.java Mapper for plurals data (which is
supplemental but can’t be mapped using regexes) IcuData.java Data structure for
holding the converted data in ICU format IcuDataSplitter.java Splits an IcuData
object into multiple objects, one for each output directory. Used by
NewLdml2IcuConverter. IcuTextWriter.java Writer for IcuData objects
CompareIcuOutput.java Compares the content of ICU data files in two directories.
ldml2icu_readme.txt README for regex files ldml2icu_locale.txt Mapper for locale
data ldml2icu_supplemental.txt Regex file for SupplementalMapper
ldml2icu_dir_mapping.txt Backup mapping of ICU data paths to output directories.
Used if NewLdml2IcuConverter is run without using Ant
