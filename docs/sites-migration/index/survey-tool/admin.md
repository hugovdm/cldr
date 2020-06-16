# admin

General note:

*   The subpanes **don't** auto refresh. Click the tabs to reload contents.
*   password needed.
*   you can bookmark a subpane
*   To get to the Admin Panel, find the "cldr" directory (in your Tomcat server
    home). If you have viewed a recent Survey Tool page, there should be an
    "admin.html" file. It contains a link to your admin panel.

### Users

*   ### list of users currently logged in

### Threads

*   ### list of active threads

### Exceptions

*   See:
    [STroubleshooting](../../development/surveytool-info/stroubleshooting/index.md)

### Settings

*   gives the current settings
    ([cldr.properties](../../development/running-survey-tool/cldr-properties/index.md)
    *which see*)
*   also allows you to modify some items
*   CLDR_HEADING - this is the headline message (now in yellow). Use this to
    notify users that its' time to log out.

### Actions

These are buttons that perform various actions.

*   #### rawload

> This action allows you to import a copy of the production SurveyTool data to
> your local system for testing. **It erases all users and votes** from your
> local instance, hence it is only permitted for the "Local" Environment (i.e.
> not smoketest nor production).

> To use:

> 1.  Download the file http://www.unicode.org/repos/cldr-tmp2/usersa/usersa.xml
      and store it on your local disk. This contains anonymous (no name or email
      address) information.
> 2.  Download (you can use Subversion) the pxml (*proposed XML)* directory from
      <http://www.unicode.org/repos/cldr-tmp2/pxml/> to your local disk.
> 3.  From the Admin panel, click "**Actions**" and then click the "**rawload**"
      button.
> 4.  Fill in the form:
>     1.  ABSOLUTE PATH to users.xml with the path to your local users.xml file
>     2.  ABSOLUTE PATH to pxml with the path to your pxml directory
>     3.  Click the Submit button.
> 5.  This will take a few minutes. Watch your server console.
>     *   **NOTE: This process purposefully causes the SurveyTool to enter a
          "broken" state, so that it isn't used in an inconsistent manner. The
          message "WARNING: SurveyTool busted: Due to IMPORT of local data" is
          expected and due to successful import.**
> 6.  When successful, you will see something like
>     *   *"1 user files read..."*
>     *   *"136 locales loaded from
          /home/srl/workspace/cldr-tmp2/pxml//common/main and 5 locales loaded
          from /home/srl/workspace/cldr-tmp2/pxml//seed/main"*
>     *   *"... Now busting (shutting down) your surveytool so that this will be
          picked up the next time around"*
>     *   ***\[warning\] You must manually restart the SurveyTool to proceed.
          (i.e. restart Tomcat)***
> 7.  Next, you **must** restart the SurveyTool. From Eclipse, right-click the
      server instance and choose Restart.
> 8.  Your main (admin@) vetting password is unchanged, however, all other user
      accounts have been replaced by the production data.

> Note: if you require non-anonymized user data, the server has the file
> "users.xml" which has original names and email addresses. See
> {tomcat}/cldr/vetdata/users/users.xml on the server.
