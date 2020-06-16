# Building the Survey Tool (cldr-apps) under ant

***Note: those new to Survey Tool development are recommended to use the much
simpler*** [***Eclipse***](eclipse/index.md) ***setup.***

1.  Build the CLDR Tools [using the command
    line](../building-cldr-tools/index.md) (or using eclipse) to produce
    cldr.jar
2.  Download and install [Tomcat](http://tomcat.apache.org/download-60.cgi)
    somewhere (don't use spaces in your directory names-please.).
    Verify that you can view pages from this server (such as at
    http://127.0.0.1:8080 ).
3.  Configure [Manager
    access](http://tomcat.apache.org/tomcat-6.0-doc/manager-howto.html#Configuring%20Manager%20Application%20Access)
    for a user
4.  Check out <http://unicode.org/repos/cldr/trunk/> somewhere. This will be
    referred to as CLDR_DIR later.
5.  go into tools/java and run "ant all jar"
6.  go into tools/cldr-apps
    1.  Copy build-sample.properties to **build.properties**
    2.  Uncomment/edit all of the **MANDATORY** and potentially other lines in
        **build.properties** as follows:
        1.  set `CATALINA_HOME` to the root directory of your Tomcat
            installation
        2.  set `password` ( and potentially `username` if it is not 'admin' )
            to match the "Manager access" user, above.
        3.  CLDR_TOOLS shouldn't need to be set, as it is a sibling to the
            cldr-apps directory
        4.  Set other lines according to the **build.properties** column of
            [this table](jars.md), (may be out of date- 2014)
7.  ` ant web `To test compilation, run:
    ` (If there are any failures, check build.properties)`
8.  `"ant war" will build cldr-apps.war.`
9.  `Start up Tomcat ( cd tomcat/bin ; sh startup.sh )`
10. `ant deploy`Run (the first time):
    ` If all goes well, it will install onto the server, as
    http://*yourserver:8080*/**cldr-apps**`
11. Test out the above URL (substituting your server's name or 127.0.0.1 and the
    port number)-
12. If all goes well, you should see the page titled '**CLDR Web
    Applications**'.
13. **Great**, now Follow the [CLDR SurveyTool setup instructions](setup.md) ,
    remembering:
    1.  ...the location of your "cldr/trunk" checkout to be used as CLDR_DIR.
    2.  ...that you must use the tomcat/bin/startup.sh and
        tomcat/bin/shutdown.sh scripts to restart tomcat
    3.  ...that you will find 'context.xml' as a text file inside the
        tomcat/conf/ directory
