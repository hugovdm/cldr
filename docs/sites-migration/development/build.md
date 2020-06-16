# Continuous Build

\[some quick notes for now\]

*   build status @ http://unicode.org/cldr/trac/build
*   single build:
    *   validates xml
    *   builds tools
    *   runs consolecheckcldr
    *   runs core unit tests
    *   builds cldr-apps (SurveyTool)
    *   runs cldr-apps unit tests
    *   deploys SurveyTool to Smoketest

How to debug build failures from the command line on st.unicode.org

*   View the failed build, keep that page open…
*   SSH into st.unicode.org
*   "Invalidate" the build via the Invalidate button, and
*   **immediately** execute: `sh runbitten.sh -s -k`
*   This will run the build from the command line **AND** not delete the
    workspace when done.
*   After failure, you can view/interact with the build results in (for example)
    **~/build/build_cldr-all_1613**
*   Scripts used to run the build are in ~/bin-build
