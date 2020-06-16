# TestAttributeValues

This test checks the elements, attributes, and attribute values for validity,
using the DtdData.

## Attribute Values

The DTD attribute @MATCH is used to test the attribute value. It has a small set
of tests that it can perform, with a simple ability to combine tests.

If the test fails, there are two cases:

1.  The value is valid, and the DTD needs fixing to keep up.
2.  The value is invalid and a data file needs fixing.

---

Here is what a failure of type 1 looks like, when pasted into a spreadsheet
(recommended, since the tabs will separate into columns that way):

Status DtdType Element Attribute Match expression #Failures Failing values
invalid ldml language alt literal/long, secondary, short, variant 1 menu

The problem is that there is an additional value that needs to be added to the
literals in the match expression in the DTD. After verifying that the failing
value is in fact correct, it can be added to the literals to fix the problem.

---

Here is a type 2 failure.

Status DtdType Element Attribute Match expression #Failures Failing values
invalid supplementalData numberingSystem id bcp47/nu 1 segment

The cause was the following line added to supplemental/numberingSystems.xml.

<numberingSystem id=*"segment"* type=*"numeric"*
digits=*"&#x1FBF0;&#x1FBF1;&#x1FBF2;&#x1FBF3;&#x1FBF4;&#x1FBF5;&#x1FBF6;&#x1FBF7;&#x1FBF8;&#x1FBF9;"*/>

The line lists the match expression from the supplementalData.xml, which is if
you look at the source:

<!ATTLIST numberingSystem id NMTOKEN #REQUIRED >

<!--@MATCH:bcp47/nu-->

The problem was that "segment" was not a valid bcp47 -nu- value. Since it was a
value that should also have been added to bcp47/number.xml, the fix was to add
to the following line:

<type name="segment" description="Legacy computing segmented digits"
since="37"/>

---

## Leniency

*NOTE: The test may not be strict enough; sometimes there are lines like the
following, where a much tighter set of validity criteria should be used;
typically using a function like locale/*

<!--@MATCH:regex/\[a-z\](\[-\]\[a-z\]+)\*-->

## @MATCH Expressions

The expression language can change in the future; it is currently the following.

<...> marks a variable.

anyAny string bcp47/<key> Any bcp47 key in
[common/bcp47](https://github.com/unicode-org/cldr/tree/master/common/bcp47):
nu, etc. literal/<A>, <B>, ... Matches any one of <A>, <B>, ... regex/<pattern>
Anything matching<expression> using [Java
syntax](https://docs.oracle.com/javase/8/docs/api/java/util/regex/Pattern.html)
validity/<file>Matches anything in the validity files, such as validity/script
for
[common/validity/script.xml](https://github.com/unicode-org/cldr/blob/master/common/validity/script.xml).
Also validity/locale matches any valid locale.metazoneMatches a valid
metazoneset/<expression>The attribute value is split at spaces, and each is
tested according to <test>, eg set/validity/localetime/<pattern>Matches anything
that parses according to ICU's SimpleDateFormatunicodeset/<pattern>Matches
characters (and strings) in UnicodeSet(<pattern>)versionMatches a version, such
as 13.2.99range/<A>~<B>Matches numbers from <A> to <B>, such as range/3.2~5. The
numbers are doubles iff there is a dot in either <A> or <B>, otherwise must be
integers.or/<exp1>||<exp2>||<exp3>...Matches any of a number of expressions,
separated by ||. Best to put any literal expression last.

Note: for NMTOKENS and other attribute values split by spaces, use
set/<expression>

## Debugging

A convenient place to put a breakpoint is at the second call to
\[dtdData.getValueStatus\] in TestAttributeValues. It is set up to repeat the
call if there is an invalid result.
