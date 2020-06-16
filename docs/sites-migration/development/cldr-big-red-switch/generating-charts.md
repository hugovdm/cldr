# Generating Charts

## Generate

[TOC]

1.  Make sure the version is right in ToolConstants (eg 30).
    1.  Make sure the *last* number (eg 29.0) is in CLDR_VERSIONS
    2.  When updating that, also add a new folder with that number (eg 30) in
        cldr-aux/charts
2.  Use the right status value:
    1.  -DCHART_STATUS=beta (*default*, uses trunk, calls it β)
    2.  -DCHART_STATUS=trunk (uses trunk, no β. Used at the end of the release,
        but before the final data is in cldr-archive)
    3.  -DCHART_STATUS=release (only uses the cldr-archive, no β)
3.  Run GenerateAllCharts. The results for each will be in
    **...cldr-aux/**by_type/names.currency.html and so on.
    1.  If there is a failure in the Transform charts, it is often because of a
        missing dependency.
        *   Goto CLDRTransforms.DependencyOrder, and add an item there.
        *   Example: addDependency("Latin-Bopomofo", "Latin-NumericPinyin");
4.  Spot-check for sanity.
    1.  Start from the main page (eg
        http://www.unicode.org/cldr/charts/28/index.html), and click on each of
        those links.
    2.  On each of the subpages, take the first chart on each page, recursively.
    3.  Use the "Index" link to go back up (not the back button), and make sure
        it goes to the right version of the page.
5.  Check into SVN.
    1.  Compensate for SVN's brain-dead handling of the mime-type.
        1.  In Eclipse, select the enclosing folder.
        2.  Right-click > Team > Set Property
        3.  Property Name: svn:mime-type
        4.  Enter a text property: text/html
        5.  Set Property recursively: ON
        6.  OK
        7.  Then select each of the .css files, and reset the text property to
            text/css.
6.  In the printout from ChartDelta, there is a listing of the sizes
    1.  Something like the following:
        1.  newItems        17.70%
        2.  deletedItems    3.26%
        3.  changedItems    3.32%
        4.  unchanged       75.72%
        5.  total   702800
    2.  Add those new figures to the release page (*except skip "unchanged"*).

> ### *Start/End of Release*

1.  At the end of the release
    1.  Generate with -DCHART_STATUS=trunk
    2.  Change the page <http://cldr.unicode.org/index/charts> to add the new
        release
    3.  *Check the redirection links on
        [test-chart-links](test-chart-links.md).*
    4.  On index.html; open it, and fix the version (eg to 25β => 25)
2.  At the start of the release:
    1.  change ToolConstants to bump these values as appropriate.
        1.  DEFAULT_CHART_VERSION = "28";
    2.  In order for chart generation to work properly, you must have archive
        versions.
        1.  You must have versions that match every ToolConstants.CLDR_VERSIONS
            in a directory.
        2.  Best is to download any missing ones from the public zip files, eg
            http://unicode.org/Public/cldr/27/.
        3.  The directory name must match whatever your "ARCHIVE" environment
            variable is set to.
            1.  For example, if ARCHIVE is set to "/foo", then you would need to
                have CLDR 24.0 checked out as "/'foo/cldr-24.0" for chart
                generation to work.
    3.  generate as above. This will change the version to (say) "25β" visible
        on each page.
    4.  Spot check for sanity as well, as above.
    5.  copy index.html from the last version to the current version; open it,
        and fix the version (eg to 25β)
    6.  checkin to SVN
    7.  *Check the *redirection* links on
        [test-chart-links](test-chart-links.md).*

## Modifying the chart programs

The chart programs have grown over time, and need some cleanup. For example, the
supplemental charts duplicate code that is now in SupplementalDataInfo.

**ShowLanguages.** The messages that they use are in a file
util/data/chart_messages.html. The right cell contains the key, which is
extracted by lines like:

PrintWriter pw = new PrintWriter(new FormattedFileWriter(index, "Zone \\u2192
Tzid", null));

The key will be zone_tzid, in this case.
