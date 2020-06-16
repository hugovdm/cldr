# Testing Transforms

1.  run org.unicode.cldr.test.**TestTransformsSimple**.
    1.  Check for failures and fix.
2.  before the next step, make sure you add to CLASSPATH:
    $ICU4J_ROOT/main/tests/translit/out/bin/
3.  run org.unicode.cldr.test.**TestTransforms**.
    1.  Check for failures and fix.
    2.  If you have problems:
        1.  use -Dverbose=true to see what is happening
        2.  This fellow actually runs the ICU tests indirectly, so the regular
            ICU test framework controls work, like -n and -v.
    3.  There is currently a bug in ICU that causes TestRegistry to fail, giving
        you 2 false negatives. Ignore this.
4.  run org.unicode.cldr.tool.**GenerateTransformCharts**.
    1.  Check in the results (the charts in diff), then review [Transform
        Charts](http://www.unicode.org/cldr/data/charts/transforms/index.html)
        for any problems.
    2.  *In order for the changes to the charts to be permanent, you have to
        tell Steven to update the server code and data; otherwise these will be
        overridden by the chron job.*
5.  run org.unicode.cldr.icu.**ConvertTransforms**
    1.  This converts to ICU data format in the directory specified by **-d
        <targetDir>**
    2.  Spot-check the results.
6.  run org.unicode.cldr.test.TestTransforms again.
    1.  This time, use the VM option **-Dfiles=<targetDir>**. This will cause it
        to run on ICU data you just generated.
    2.  Check for failures and fix.
7.  get yourself a cupcake.
