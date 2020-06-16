# Subeclipse Setup

## Updating Eclipse & SVN for CLDR (TODO: Update for Git)

1.  Go to <http://www.eclipse.org/>
2.  Downloads
3.  Pick Eclipse IDE for Java EE Developers (eg Mac OS X 64 Bit)
4.  download
5.  If you download the wrong one,
    1.  Help>Install
    2.  <http://download.eclipse.org/webtools/repository/indigo> (or whatever
        the version is)
    3.  Web Tools Platform (latest version)

## Subclipse

1.  Go to http://subclipse.tigris.org/ > Downloads
2.  Find the latest release that works with Eclipse of your version. Eg.
    <http://subclipse.tigris.org/update_1.8.x>

## Open Eclipse

1.  Help>Install new software...
2.  Paste subclipse URL above in “Work with:”
3.  Select both Subclipse and SVNKit
4.  Next, Next, Accept, Finish
5.  Ignore warnings about unsigned content
6.  Restart
7.  Go to Preferences > Team > SVN > SVN Interface Client
8.  Pick SVNKit …
9.  If you don’t do this, you get the picture below.

## Load CLDR

1.  File > Import > Checkout projects from SVN > Next
2.  Create new Repository, use svn+ssh://unicode.org/repos/cldr
3.  Close error box
4.  See box “Enter SSH Credentials”
5.  Enter user and private key (see XXX)
6.  Port 22
7.  Get strange message.
8.  Say Ok
9.  You should get the project loaded up in {workspace}/cldr

*Do the same with cldr-apps; even if you don't use it, you want refactoring to
cover both projects!*

## Make Java Projects

1.  File - Import > General > Existing Projects into Workspace
2.  Select Root Directory: put in {workspace}/cldr/tools
3.  DON’T check “Copy projects into Workspace”
4.  Do this for both cldr-tools and cldr-apps.

## Go Back

Go back to [Eclipse Setup](index.md), and continue after "**Preferences**".
