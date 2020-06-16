# Transforms

To do a simple test of transforms while modifying, run
test/TestTransformsSimple. You'll need to update it to add tests for the
transform you're interested in.

To convert to ICU format, run icu/ConvertTransforms. It will create a set of
files in the following directory (you can change the target with parameters).

{cldr}/dropbox/gen/icu-transforms/

Then run test/TestTransforms. It will take all of those ICU format transforms,
and run the ICU tests using them. What it does internally is to register the
CLDR transforms on top of the ICU transforms, then run the tests. You need to
supply the ICU args, typically

-t -e -n

Use -e10 for an exhaustive test.

If these look ok, then you can copy the generated transforms to ICU.
