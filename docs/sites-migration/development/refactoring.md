# Refactoring CLDR code

When refactoring, especially low-level code, you need to watch for a few things.

1.  The unit tests are not complete, so just running them is not sufficient.
    Also run other tools:
    1.  console check
    2.  new ldml to icu tool
    3.  generate charts
    4.  generate item counts
    5.  \[TBD add others\]
2.  Many of the CLDR APIs are used in the unicodetools project, so refactoring
    them just in CLDR can cause breakages.
    1.  When you use Eclipse refactoring tools, make sure you have the
        unicodetools project available also, so that changes are made there.
    2.  If you don't work on unicodetools, ask someone (Mark or Markus) to do
        the refactoring.
