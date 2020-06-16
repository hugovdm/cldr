# Updating Code Process

So you want to update CLDR code/data in the [CLDR
Repository](cldr-repository-access/index.md)?

1.  Make your changes.
2.  Test locally
    1.  XMLValidate
    2.  ConsoleCheckCLDR...
    3.  cldr-tools unit tests (TBD)...
    4.  cldr-apps unit tests (TBD)...
3.  Commit your changes
4.  The build process [here](http://unicode.org/cldr/trac/build) will pick up
    your changes - watch to make sure there are no failures
5.  If the build succeeds, the Smoke Test Survey Tool will be restarted using
    the new code/data.
    1.  For CLDR 22, see the "**[ST Bringup 22](http://goo.gl/2vbDX)**"
        (protected) Google Doc for discussion
6.  To promote the Smoke Test code to production, there is a link on
    **kwanyin/cldr-build** - but, it may require discussion with the cldr-dev
    mailing list before promoting a change. As well, promoting the change will
    kick off currently active users.
