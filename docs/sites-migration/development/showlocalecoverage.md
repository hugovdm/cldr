# ShowLocaleCoverage

The ShowLocaleCoverage program is used to:

1.  check that we have reached full modern coverage for the CLDR org locales
    (while ST is running)
2.  generate raw material for the growth chart on the release page.

Make sure that you have an archive of all CLDR versions set correctly. It should
be directory containing each of the cldr versions, like:

*   cldr-26.0
    *   common
        *   bcp47
        *   casing
        *   collation
        *   ...
    *   keyboards
*   cldr-25.0
    *   common
    *   keyboards
*   ...
*   cldr-1.1.1
    *   common
        *   dtd
        *   main

The top level will look like:

    *   cldr-1.1.1
    *   cldr-1.2
    *   cldr-1.3
    *   cldr-1.4.1
    *   cldr-1.5.1
    *   cldr-1.6.1
    *   cldr-1.7.2
    *   cldr-1.8.1
    *   cldr-1.9.1
    *   cldr-2.0.1
    *   cldr-21.0
    *   cldr-22.1
    *   cldr-23.1
    *   cldr-24.0
    *   cldr-25.0
    *   cldr-26.0
    *   cldr-27.0
    *   cldr-28.0
    *   cldr-29.0
    *   cldr-30.0
    *   cldr-31.0
    *   cldr-32.0
    *   cldr-33.0
    *   cldr-33.1
    *   cldr-34.0
    *   ...

The directories in each release will vary. Make sure that you have the keyboards
directory for as many as have it.

Then make sure that you have the the following settings

-DARCHIVE=<that-directory>

-DCLDR_GEN_DIR=<output-directory>

You might also need to bump up your memory in Eclipse, since it reads all
versions of CLDR, and all the files (except regional variants).

You can set this up globally in Eclipse using Preferences... \[search for
Installed JREs\] > Edit (on yours), or set them in the configuration of the
programs

## Growth Graph

Go into Eclipse in the Run Configuration… for ShowLocaleCoverage and set up the
arguments for the right directory.

Required:

-g to select growth

Optional:* Useful for debugging the tool, making sure the directories are set up

-f xxx to filter to just some locales (matching the regex xxx).

Reset the DEBUG switch at the top of the file

**Generates `tsv/locale-growth.tsv` (you can override the target directory with
-t ddd).**

It should look something like the following (tab delimited). Make sure that the
first version is correct for the release page you are generating (eg, "2017"
below).

0123…201710.99955823880.99953502790.9995098039…20160.70420958350.6888961180.67272727270.6680742163…

Create a copy of the latest growth chart spreadsheet, such as [CLDR v28
Growth](https://docs.google.com/spreadsheets/d/13BYViL9WU6wIcR6ZEj3Ip9p7v4rXBDm-F0WfjUhaYXo)
to a new version **CLDR vXX Growth**. Share with the CLDR group. Open the copy,
and go to the tab RawData (look at the bottom) of the spreadsheet. Select cell
A1.

Open showLocaleCoverage.txt, select all (^A) and copy. Go to the spreadsheet and
paste (with ^-shift-V, or "paste values only").

Switch to the first tab, and you should see a nice chart. Embed it as below.

## Embedding

To embed a chart into a release page, open for editing, then Insert > Chart.
Pick the chart that you just made.

Use:

*   no border
*   no title
*   width: 800
*   height: 400

Once added

1.  Align Center with the tool.
2.  Save
3.  Review to make sure formatting is ok.

**NOTE: it works out better to take a snapshot of the graph, and then just
insert that.**
