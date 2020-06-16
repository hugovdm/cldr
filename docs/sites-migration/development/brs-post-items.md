# CLDR BRS Post Items (Section E) for Rick

**Actions for Rick, prior to Alpha**

**A25**

1.  <http://cldr.unicode.org/index/downloads/cldr-XX> — In the header, put the
    SVN Tag link on the Data item On the release page, e.g.
    http://cldr.unicode.org/index/downloads/cldr-35
    set the string and link for "SVN Tag" field to "release-35-alpha" and a SVN
    link such as http://www.unicode.org/repos/cldr/tags/release-35-alpha/ and
    add that link also to the "Data" field.
2.  <http://cldr.unicode.org/> — In the "News" section at the top of the page,
    add a new yellow top row for the alpha (for the beta/release, reuse that
    row). Remove old releases from the table (major ≤ alpha-2 - leaving only 2
    recent major releases), and de-yellow the remainder except for the top row.
3.  <http://cldr.unicode.org/index/downloads> — Add a new row (below "Latest"
    and "Dev") for the new alpha. Copy various links as needed. (It will stay
    the same for the beta, then change to be the release row).

**Actions for Rick, section "E" of the CLDR Release BRS**

D10
Remove the yellow from UTS#35 draft, and clean up everything for posting. Run
W3C validations and link checks on all parts. Make sure links to images are
correct before posting, and create a symlink to the image directory within the
reports/tr35/tr35NN directory. Make sure that the revision is headed with
"updated for" rather than "proposed update for". Double check the text and links
for the DTD and versions in the header. Check into SVN. Then post as final UTS
#35 on unicode site. Double-check the DTD and header pointers again when
finished.

E03
Create a new directory, e.g. <http://unicode.org/Public/cldr31/> and populate
with the zip files from John. Double check filenames core.zip, tools.zip,
keyboards.zip. (Add json.zip and json_full.zip if John made them.) For each of
the zip files, create a *symlink* that is the versioned name of the file. E.g.
make cldr-tools-30.0.3.zip a symbolic link to tools.zip. Etc.

E04
Update link to "latest" by modifying /home/httpd/htdocs/.htaccess to change the
redirect of /Public/cldr/latest

E05
Change the chart redirects to point to the new versions. For testing, change the
links on the page to the right to the new version, eg /22.1/ => /23/. Then spot
check. Make the beta-charts links point to 'not found' page (until we regenerate
beta-charts). ~~Chart redirects are found in /home/httpd/htdocs/cldr/.htaccess ;
of the form "Redirect /cldr/charts
http://unicode.org/repos/cldr-aux/charts/22.1/index.html".~~ Also see the
"**RewriteRule**" section in **/etc/httpd/conf/extra/httpd-rewrite.conf** where
it points cldr/charts to the "latest" and "dev" release explicitly (around line
55 of the special conf file). There are 2 redirects, one for dev and one for the
new version that's being released. See also the "stable links info" on Sites:
<http://cldr.unicode.org/stable-links-info>. This must be updated and the server
gracefully restarted. (Command "apachectl graceful" works.)

*Bug-How-To-Links:*
<https://sites.google.com/site/cldr/development/cldr-big-red-switch/test-chart-links>
(Copy out the text of the test links on that page; Change the {latest} to be
current release, and any prev release numbers to the current one, the test them
all.) See also info here and update DEV and LATEST as needed:
<https://sites.google.com/site/cldr/stable-links-info> Verify links on
<https://sites.google.com/site/cldr/development/cldr-big-red-switch/test-chart-links>
work.

E06
Verify that the links on the release page (e.g.
<http://sites.google.com/site/cldr/index/downloads/cldr-28> ) are correct, and
Draft is removed from the text. At this time also make sure the "news" item on
<http://cldr.unicode.org> is updated, at the top of the page -- for all
releases, alpha, beta, and final.

E07
Modify <http://sites.google.com/site/cldr/index/downloads> so that it includes a
new row on the top (Latest:), with the information from the current release (eg
<http://sites.google.com/site/cldr/index/downloads/cldr-27> ). Might be easiest
to do in HTML mode. Most of the ***latest*** row should remain standard, but
some of the *targets* of those anchors need to be updated for each release.
Click through all and test them.

E08
Change the dtd redirection, in /home/httpd/htdocs/cldr/dtd/.htaccess so that
http://www.unicode.org/cldr/dtd/(X+1)/ points to
<http://www.unicode.org/cldr/data/common/dtd/>
http://www.unicode.org/cldr/dtd/X/ is new. Upload the tagged dtd files there.
Edit /home/httpd/htdocs/cldr/dtd/.htaccess and bump the version number to "X+1".
To verify that these are properly accessible, type the new dtd (X+1) URL into a
browser, and if you get to the head of CVS, it's correct. (The tagged DTD files
are in core.zip, in case they aren't supplied separately; get them from the zip
file under common/dtd directory.)

E09
Update https://sites.google.com/site/cldr/index/charts and other pages that
refer to version files directly. List here:
https://sites.google.com/site/cldr/index/downloads/dev

*Bug-How-To-Links:*
In the charts page, add a row to the top of the table for the new release.

E13
Update the sidebar for the release, eg: CLDR 1.8 Schedule: 2009-NN
=>
Latest Release: CLDR 1.8
and gray out the schedule. NOTE: Only the "site owner" can change the sidebar.
Go to "edit site layout" in the "More" pulldown, then click on the Milestones
header to edit that section. ~~List the latest release (26), and delete all but
2 releases. Change "nn Release" to "nn Released" and put a link on "Released" to
the release page.~~

NEW: Go to the bottom of the cldr.unicode.org home page and find the table for
"Regular Semi-Annual Schedule". In HTML mode, copy which ever half of the table
is for the upcoming release (spring or fall), and update the sidebar with that
section of the table by pasting in the different HTML blob of the table.

E14
Create a new blog page from
<http://sites.google.com/site/cldr/development/cldr-big-red-switch/draft-press>
; publish the blog, and update the Unicode Home page. The announcement listing
should be in New Releases, not Other News. Tweet a little announcement pointing
to the blog as needed. (Note: Mark and others on the ed committee can update and
edit the blog/twitter as l2doc@unicode.org.)

E15
As an announcement, send contents of
<http://sites.google.com/site/cldr/development/cldr-big-red-switch/draft-press>
to all the Unicode mailing lists -- Usually first make sure the list is up to
date by logging in as root and running "make-announcement-list.sh". Mark,
Steven, Rick, and John are all able to send announcements to
"announcements@unicode.org". (NOTE: best to double-buffer and check the HTML
before sending to the list; HTML pasted in from sites and other places often has
quirks.)

*Bug-How-To-Links:*
Normal announcement mechanism is described in:
<http://www.unicode.org/~book/announce-brs.html> (for Rick or others to follow)

E16
Verify that these are empty before trunk opens:
<http://unicode.org/cldr/trac/report/22>
<http://unicode.org/cldr/trac/report/51>
<http://unicode.org/cldr/trac/report/52> -- and then Notify cldr@unicode.org
that the trunk is open: e.g., say "Now that CLDR X.Y has been released, the SVN
trunk ( http://unicode.org/repos/cldr/trunk ) is open for commits towards the
next release." Use a subject line something like: "CLDR X.Y - trunk now open",
where X.Y is the next release. If report 51 is not empty, verify that anything
remaining is either the result of a misticketed item, or that any commits had
net zero effect on trunk ( for example, a change that was later backed out ).

#### F02

Create a new stub release page for the next release by copying the previous page
(...downloads/cldr-31 or whatever) and state that it's a stub. Retain the
top-level headers from the previous release page. Yellow some sections for the
update.

Fix the links as followed (to **Link Nonfinal**). (When the release is done, fix
to **Link Final**).

*Note: replace 99 by target release number, 999 by target release number minus
1, and 88 by final tr35 revision.*

**Head** **Contents** **Link Nonfinal** **Link Final** **No.** 99 none none
**Date** 2018-MM-DD none none **Rel. Note** v99
<http://cldr.unicode.org/index/downloads/cldr-99> same **Data** CLDR99
<http://unicode.org/Public/cldr/99/> \*The target directory needs to be created
now as empty, with a readme file. same **Charts** Charts99
<http://www.unicode.org/cldr/charts/99/> same **Spec** LDML99
<http://unicode.org/reports/tr35/proposed.html>
<https://www.unicode.org/reports/tr35/tr35-88/tr35.html> **Delta** Δ99
<http://unicode.org/cldr/trac/query?resolution=fixed&milestone=99&group=component&max=999>
same **SVN Tag** release-99 <http://unicode.org/cldr/dev>
<http://www.unicode.org/repos/cldr/tags/release-99/> **DTD Diffs** ΔDTD99
<http://unicode.org/cldr/trac/changeset?reponame=&new=HEAD@trunk/common/dtd/&old=HEAD@tags/latest/common/dtd/>
<http://unicode.org/cldr/trac/changeset?reponame=&new=HEAD@tags/release-99/common/dtd&old=HEAD@tags/release-999/common/dtd>
**DTD Δs** 99
<http://www.unicode.org/cldr/charts/99/supplemental/dtd_deltas.html> same

Near the top, add this line:
**This version is currently in development. See the [latest
release](http://cldr.unicode.org/index/downloads/latest).**

Update these two pages as required with the dev version pointer to the new page:
[ http://cldr.unicode.org/index/downloads/latest
](http://cldr.unicode.org/index/downloads/latest)
[
http://cldr.unicode.org/index/downloads/beta](http://cldr.unicode.org/index/downloads/beta)

*Also create the Data folder so that the link doesn't fail, and have the charts
made so that link doesn't fail.*

F04
Update all of the "CURRENT" reports in trac to point to the new current
milestones. Make sure $user isn't replaced by your name. The affected reports
are (52, 61, 66, 76, 77, 80) and (62, 63).

ALPHA PAGE TABLE HEADING

When making an "alpha" release page, check the header info in the table. Before
the release, some links should go to "dev" version rather than a non-existent
final version.

Rel note = dev version
Data = no link
Charts = dev version
Spec = proposed
Delta = link to the query for milestone
SVN Tag = dev version
DTD delta = "trunk" version
