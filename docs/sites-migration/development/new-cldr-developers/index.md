# New CLDR Developers

Here is a quick overview of what you need to know to do development work on
CLDR.

First, you need to have accounts set up for you on:

1.  **Jira** — for getting and handling bug reports
2.  **GitHub** — for submitting code / data
3.  **cldr-dev** — for discussions of issues, questions, etc. — if you will be
    joining the TC.
4.  **Google Docs** — to view/edit the CLDR agenda and internal documents — if
    you will be joining the TC.
5.  **Google Sites** — only if you are going to edit this website

If you don't get emails about these, contact Rick or other CLDR contacts. It is
handy, though not necessary, for you to use a gmail account for the last two of
these. Many people use a different account than their internal company email
address; you just have to link them with <https://accounts.google.com/SignUp>.

*Warning: some of these pages get stale. Ask questions on cldr-dev if you run into problems; you or the responder should also fix the stale page.*

Next, get your Eclipse environment set up properly.

1.  <http://cldr.unicode.org/development/eclipse-setup>
2.  <http://cldr.unicode.org/development/running-survey-tool/eclipse>

**Run the CLDR tests to be sure they pass before beginning work**:

Command line:

1.  Be at root of SVN working directory
2.  cd tools/java
3.  ant all
4.  cd ../cldr-unittest
5.  ant check
6.  If you see test errors, for instance TestBasic/TestDtdComparison fails, run
    only the failing test like so:
    **ant -Druncheck.arg="-v TestBasic/TestDtdComparison" check**
    The -v tells test script to show stack trace at the test failure for
    debugging.
7.  To get all parameters that could be passed at runcheck.arg, run
    **ant -Druncheck.arg="-?" check**

Via eclipse:

1.  Go [here](http://cldr.unicode.org/development/eclipse-setup#TOC-Test)

Once you are all set up, be sure to read the development process, for how to
handle tickets, when you can't make changes, etc.

at: <http://cldr.unicode.org/development/development-process> (TBD update for
migration to Jira/Github)

---

The table below points to documentation for various tasks.

**Task to completeLink to documentation** moving new CLDR data over to ICU by
editing
ldml2icu_locale.txt<http://cldr.unicode.org/development/coding-cldr-tools/newldml2icuconverter>performance
work<http://cldr.unicode.org/development/perf-testing>survey tool database
work<http://cldr.unicode.org/development/running-survey-tool/cldr-properties/db>

Other useful pages are under [CLDR Development Site](../index.md); you can also
use the search box.

[UTS #35: Unicode Locale Data Markup Language
(LDML)](http://www.unicode.org/reports/tr35/) is the specification of the XML
format used for CLDR data, including the interpretation of the CLDR data.
