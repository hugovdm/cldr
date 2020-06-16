# Adding Transliterators

For each transform:

1.  There should be a .xml file with rules, and a corresponding .txt file with
    tests.
2.  Put the .xml file in workspace/cldr/common/transforms
3.  Put the .txt file in
    workspace/cldr/tools/cldr-unittest/src/org/unicode/cldr/unittest/data/transformtest/
    1.  Note that the .txt file may look reversed if it is RTL, since the 2
        fields will show up from right to left.
4.  Run org.unicode.cldr.unittest.TestTransforms and verify that it works
    1.  Then run Run org.unicode.cldr.unittest.TestAll, just to make sure
    2.  If either fails, communicate back to the author any problems, go back to
        step 1
5.  Check in.
