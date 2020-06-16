# Voting History

The voting history is in <http://www.unicode.org/repos/cldr-aux/voting>, in
versioned directories. The subdirectories of each version are:

pxmlProposed data, with alt="proposed..." values for each user who voted.
*Example:*

<localePattern alt="proposed-u1094-">{0} ({1})</localePattern>

<localePattern alt="proposed-u1530-">{0} ({1})</localePattern>

<localePattern alt="proposed-u1803-">{0} ({1})</localePattern>

Note: you need to copy dtd.xml into common/ here if you want to run tools that
use CLDRFile on this directory directly.

usersaContains the information about users (their level and organization) that
is necessary for resolving voting. Does not contain email addresses.
*Example:*

<user id="133" level="tc" org="google" locales="\*"/>

There's a private one which also has email addresses - authorized users can
fetch it from the svn repo
`svn+ssh://unicode.org/repos/cldr-vetdata/users/users.xml`

vxmlVetted data, with the voting resolved and the best item picked according to
VoteResolver. These are the files that will go into CLDR when the data is
imported from the ST into XML, so they have exactly the same format.
Note: you need to copy dtd.xml into /common here if you want to run tools that
use CLDRFile on this directory directly.

Note: it appears that the directories fxml/, rxml/, and xml/ are obsolete (they
don't have anything but the directories, no xml files).
