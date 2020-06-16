# Spec Diffs

Once [Cleaning up the spec](index.md) and the changed/removed styles are fixed,
you can compare the old and new versions of a Part using the W3C HTML diff
program. The following links use that tool to compare trunk with the current
tr35/

*   Part 1: [Core specification
    ](http://services.w3.org/htmldiff?doc1=http%3A%2F%2Fwww.unicode.org%2Freports%2Ftr35%2F&doc2=http%3A%2F%2Funicode.org%2Frepos%2Fcldr%2Ftrunk%2Fspecs%2Fldml%2Ftr35.html)(languages,
    locales, basic structure)
*   Part 2: [General
    ](http://services.w3.org/htmldiff?doc1=http%3A%2F%2Fwww.unicode.org%2Freports%2Ftr35%2Ftr35-general.html&doc2=http%3A%2F%2Funicode.org%2Frepos%2Fcldr%2Ftrunk%2Fspecs%2Fldml%2Ftr35-general.html)(display
    names & transforms, etc.)
*   Part 3: [Numbers
    ](http://services.w3.org/htmldiff?doc1=http%3A%2F%2Fwww.unicode.org%2Freports%2Ftr35%2Ftr35-numbers.html&doc2=http%3A%2F%2Funicode.org%2Frepos%2Fcldr%2Ftrunk%2Fspecs%2Fldml%2Ftr35-numbers.html)(number
    & currency formatting)
*   Part 4: [Dates
    ](http://services.w3.org/htmldiff?doc1=http%3A%2F%2Fwww.unicode.org%2Freports%2Ftr35%2Ftr35-dates.html&doc2=http%3A%2F%2Funicode.org%2Frepos%2Fcldr%2Ftrunk%2Fspecs%2Fldml%2Ftr35-dates.html)(date,
    time, time zone formatting)
*   Part 5: [Collation
    ](http://services.w3.org/htmldiff?doc1=http%3A%2F%2Fwww.unicode.org%2Freports%2Ftr35%2Ftr35-collation.html&doc2=http%3A%2F%2Funicode.org%2Frepos%2Fcldr%2Ftrunk%2Fspecs%2Fldml%2Ftr35-collation.html)(sorting,
    searching, grouping)
*   Part 6: [Related Information
    ](http://services.w3.org/htmldiff?doc1=http%3A%2F%2Fwww.unicode.org%2Freports%2Ftr35%2Ftr35-info.html&doc2=http%3A%2F%2Funicode.org%2Frepos%2Fcldr%2Ftrunk%2Fspecs%2Fldml%2Ftr35-info.html)(supplemental
    data)
*   Part 7: [Keyboards
    ](http://services.w3.org/htmldiff?doc1=http%3A%2F%2Fwww.unicode.org%2Freports%2Ftr35%2Ftr35-keyboards.html&doc2=http%3A%2F%2Funicode.org%2Frepos%2Fcldr%2Ftrunk%2Fspecs%2Fldml%2Ftr35-keyboards.html)(keyboard
    mappings)

You will need to manually set the encoding in your browser to UTF-8 (and the
tool still doesn't get it quite right). The w3c tool has many false positives
(<pre> and <table> often fool it) also, so you will see cases like:

Roundtrip ~~mappings—the~~ mappingsâ€”the ability...

But it should allow you to double check that the Modifications are correct for
your Part.
