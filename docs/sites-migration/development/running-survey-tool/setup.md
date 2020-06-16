# SurveyTool Step-by-step setup

### (Prerequisite: you must first be able to see the "CLDR Web Applications" webpage using either [Eclipse](eclipse/index.md) or [Ant](ant.md) based setup)

### Step by Step Configuration

*(Ant users: The instructions and video assume Eclipse. You will find context.xml in the tomcat../conf directory, and you will have to restart Tomcat from the command line. Sorry.)*
Video: <http://www.youtube.com/watch?v=CCirfKI0TdQ>

1.  (video time: 0:39) Right-click on the "cldr-apps" project,
    choose Run-as->Run On Server
2.  1:27 you should see the "CLDR Web Applications" appear, stating that the
    SurveyTool is in setup mode.
    Click on CLDR Survey Tool
3.  1:46 you will see "Administrator: please open the file
    ==/..../admin.html==". Click on this link, or, open the file to which it
    refers. (the link may not work in your browser due to security reasons.)
4.  1:52 click on the "Setup" link in the admin.html local file.
5.  2:08 You should see "SurveyTool Configurator .. Set Parameters".
    1.  *(If you see a message which says "The SurveyTool is not in Setup mode", don't worry, just do the following:*
        *#1 click on the "go into setup mode" button. You should see "Now restart the server", so:*
        *#2 in the Servers tab of Eclipse (Window menu -> Show View -> Other.. -> Servers),*
        *right-click on "Tomcat ...,Server at localhost" and choose Restart"*
        *#3 refresh the "Now restart the server" page, it should now say
        "SurveyTool Configurator".)*
    2.  You can learn more about these properties at this page: [cldr.properties](cldr-properties/index.md)
6.  2:09 - the **CLDR_VAP** is your master/admin password. You can leave it as
    is or change it.
    (If you change it, delete the "admin.html" file so that it will be recreated
    with the correct password.)
    Click Save and Continue to go to the next page..
7.  2:18 - **CLDR_DIR** - type in the full path to the root where you [checked
    out CLDR](../cldr-repository-access/index.md) - this directory must contain
    "common", "seed", etc.
    Example 1: if you checked out individual directories in eclipse piecemeal,
    give your workspace path here. ( /home/user/**workspace** ).
    Example 2: if you checked out all of CLDR somewhere, give that path. (
    /home/user/src/**cldr-trunk**/ ).
    ( If you leave the default value, you will be prompted to check-out a new,
    separate copy of CLDR.)
    Click Save and Continue to go to the next page...
8.  2:39 - **CLDR_OLDVERSION** - Type in the suggested "old" value. This is the
    "previous" CLDR version.
    Click Save and Continue to go to the next page...
9.  2:44 - **CLDR_NEWVERSION -** Type in the suggested "new" value. This is the
    "new" CLDR version.
    Click Save and Continue to go to the next page...
10. 2:54 - **CLDR_PHASE** - Leave this at "BETA"
    Click Save and Continue to go to the next page...
11. 2:59 - **CLDR_MESSAGE** - leave this blank.
    Click Save and Continue to go to the next page...
12. 3:04 - **CLDR_HEADER** - this the Welcome message given at the top of each
    page. Change it or remove it entirely, or leave it alone.
    Click Save and Continue to go to the next page...
    ***There will be a delay at this point - the OLD and NEW CLDR versions are
    automatically being checked out.***
13. *3:38 -If you see an X next to CLDR_DIR Verifying CLDR_DIR - if CLDR_DIR is not valid, you will be given the option and guidance to execute a "svn checkout" to make CLDR_DIR valid. Then, refresh the webpage.*
    *(**Recommended:** If your CLDR_DIR is already valid, you can skip this
    step.)*
14. 4:51 - if CLDR_DIR shows up with a checkmark next to it. it is now valid and
    you can continue.
15. 4:53 - Setting up a database.
    **Recommended**: use Derby (embedded db, no setup)
    Derby#1 5:19 select the entire `==<Resource name=
    ............................ ...cldrdb" />== `chunk inside the thin black
    box.
    Derby#2 Copy.
    Derby#3 5:22 hit Control-Shift-R ( Command-Shift-R ) and search for
    **context.xml**.
    *(It is inside the Servers project on the left hand side of your Eclipse
    Projects*)
    ***Less recommended**: use MySQL ( more complicated, but identical to production) ---*
    ***MySQL #1#2#3 ( hit the "MySQL Configurator" button and follow the instructions, also see [this page](cldr-properties/db/index.md)***
    ***The configurator will finish with a chunk of XML in a dialog for you to
    copy.)***
    #4 5:29 Paste the chunk of text just before the closing </Context> tag in
    the context.xml file.
    #5 Save this context.xml file
    #6 5:52 Right click on the Tomcat server and Restart
    #7 6:07 Reload the webpage- Now your Database should be valid! (Should see a
    checkmark next to 1 and 2 in the box)
16. 6:13 - click Remove Maint Mode
17. 6:20 - Restart your server one more time..
18. 6:48 - SurveyTool is now running!
19. 6:52 - from "admin.html" (reload admin.html if you had deleted it) you can
    click the "Admin Panel" link to login to the SurveyTool as administrator.
    1.  Note 1: There's a "Create Test User" link in the admin panel, that will
        let you create a random test user.
    2.  Note 2: to login as admin, the email is "**admin@**" and the password is
        your CLDR_VAP password.
