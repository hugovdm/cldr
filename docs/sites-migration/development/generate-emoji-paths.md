# SBRS: Update emoji translations & ordering

1.  Run unicodetools GenerateEmoji with the beta options
2.  Make sure that org.unicode.tools.emoji.unittest.TestAll runs successfully,
    with -Demoji-beta.
3.  Run unicode tools: org.unicode.tools.emoji.GenerateCldrData
4.  Copy each list of data from console output into (respectively)
    1.  annotations/root.xml
    2.  annotations/en.xml
    3.  emoji-test.txt into org.unicode.cldr.util.data.emoji
5.  Run org.unicode.tools.emoji.CopyImagesToCldr.java to add images to ...
    cldr/tools/cldr-apps/WebContent/images/emoji/
    1.  These are the ones that show up in the info panel of the survey tool.
6.  Update the collation/root.xml using
    unicode/draft/emoji/charts-XX/emoji-ordering-rules.txt
7.  Change the name composition algorithm if necessary (for new emoji zwj
    sequences)
    1.  It may have also been modified during the emoji development.
    2.  Ensure that the documentation of composition of names (for new
        components like hair styles) in LDML is updated to match what is in
        org.unicode.cldr.util.Annotations.
8.  Run tests
    1.  You may get an error in testAnnotationPaths.
        1.  May need to change org.unicode.cldr.util.Emoji.SPECIALS to have
            TestAnnotations pass. These are zwj sequences whose names cannot be
            composed.
        2.  eg "\[{🏳‍🌈}{👁‍🗨}{🏴‍☠}\]"
    2.  You may also get an error in TestNames. Check the names to see what is
        happening, and whether to change the test or the data.

TODO: test that derived names are complete
