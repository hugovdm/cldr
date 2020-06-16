# Editing Release Pages

## Release Page

Each release page looks like <http://cldr.unicode.org/index/downloads/cldr-37>.

There is a row of important links at the top. These have the following contents,
with "37" in the examples to be replaced by the actual release number.

Header Links/contents during development Final version **No.** Version number
with δ (development), α or β, such as 37β Strip the beta **Date** Planned
release data, with XX for day Final release date Rel. Note
<http://cldr.unicode.org/index/downloads/cldr-37> *no change* Data
<http://unicode.org/Public/cldr/37/> *no change* Charts
<http://www.unicode.org/cldr/charts/37/> (charts themselves will have δ
(development), α or β) *no change* Spec
<http://www.unicode.org/reports/tr35/proposed.html> (will redirect to [github
page](https://unicode-org.github.io/cldr/ldml/tr35.html)) Change to specific
version, such as: <http://www.unicode.org/reports/tr35/tr35-59/tr35.html>
**WARNING: the version after the tr35- is NOT the same as the real version. Pick
it up after the spec is prepped (de-yellowing).** Delta Tickets
<https://unicode-org.atlassian.net/issues/?jql=project=CLDR AND status=Done AND
resolution=Fixed AND fixVersion=37 ORDER BY component ASC, priority DESC> *no
change* Github Tag Start with
**[master](https://github.com/unicode-org/cldr.git)**, then change to
[release-37-beta](https://github.com/unicode-org/cldr/tree/release-37-beta),
etc. `[release-37](https://github.com/unicode-org/cldr/tree/release-37)` Delta
DTDs <http://www.unicode.org/cldr/charts/37/supplemental/dtd_deltas.html> *no
change*

When you edit links, make sure that 'Open this link in a new window' is on.

## Final version

When you change to the final version, you'll fix the lines on the release page
as in the above table. Walk through the entire page and de-yellow where needed.
Check all the links and the text to make sure everything is ready.

### Downloads page

You'll then copy the header line into <http://cldr.unicode.org/index/downloads>.
To avoid messing up the table, the easiest way to do this is:

A.

1.  open the release page, eg
    <https://sites.google.com/site/cldr/index/downloads/cldr-37>
2.  go into <HTML> mode
3.  find the line with the release number cell, near the top.
4.  copy the <tr> ... </tr> (see below for example)

B

1.  open the downloads/releases page <http://cldr.unicode.org/index/downloads>
2.  select the old last release (eg 36)
3.  do Table > Insert Row Above. That will give you an empty row.
4.  put XXX into the first cell.
5.  go into <HTML> mode
6.  find the <tr> containing <td ...>XXX</td> as the first cell
7.  replace by the <tr>...</tr> that you copied in part A.

Example <tr>..</tr>

<tr>

<td style="text-align:center;white-space:nowrap">37</td>

<td
style="text-align:center;white-space:nowrap;background-color:#ffff00">2020-04-23</td>

<td style="text-align:center;white-space:nowrap"><a
href="http://cldr.unicode.org/index/downloads/cldr-37"
target="_blank">v37</a></td>

<td style="text-align:center;white-space:nowrap"><a
href="http://unicode.org/Public/cldr/37/" target="_blank">CLDR37</a></td>

<td style="text-align:center;white-space:nowrap"><a
href="http://www.unicode.org/cldr/charts/37/" target="_blank">Charts37</a></td>

<td style="text-align:center;white-space:nowrap"><a
href="http://unicode.org/reports/tr35/proposed.html"
target="_blank">LDML37</a></td>

<td style="text-align:center;white-space:nowrap"><a
href="https://unicode-org.atlassian.net/issues/?jql=project%20%3D%20CLDR%20AND%20status%20%3D%20Done%20AND%20resolution%20%3D%20Fixed%20AND%20fixVersion%20%3D%20%2237%22%20ORDER%20BY%20component%20ASC%2C%20priority%20DESC%2C%20created%20ASC"
target="_blank">Δ37</a></td>

<td style="text-align:center;white-space:nowrap"><a
href="https://github.com/unicode-org/cldr/tree/release-37"
target="_blank">release-37</a></td>

<td style="text-align:center;white-space:nowrap"><a
href="http://www.unicode.org/cldr/charts/37/supplemental/dtd_deltas.html"
target="_blank">ΔDtd37</a></td>

</tr>

### News

Go to <https://sites.google.com/site/cldr/index>, and update the News table.
Drop any news off the bottom that is more than ~5 months old.

## New Release

1.  Copy the old release page with the new URL based on the version number.
2.  Fix the header table links as per table above.
3.  Add just below See Key to Header Links a new line (fixing the version link)
    *   This version is under development: for the latest version see version
        [37](../../index/downloads/cldr-37/index.md). Some links above will not
        work until development work has started.
4.  Edit the Overview section
5.  In all other sections, replace bullet lists (and chart) by TBD

## Announcement

1.  Use release page information to create a new announcement on [Draft CLDR
    Announcements](https://docs.google.com/document/d/1_o-mGZkUgt68KqOJVV4OOWDUUzuRjp5AgwoMIKnWQ0M/edit#heading=h.tkuxaftnkqy9)
    1.  That document has old copies in gray, for comparison. So gray out the
        last one before starting anew.
    2.  But you can also consult the latest blog announcements for comparison,
        with
        <http://blog.unicode.org/search?q=CLDR+release&max-results=20&by-date=true>
    3.  Eg,
        <http://blog.unicode.org/2019/10/unicode-cldr-version-36-languagelocale.html>
2.  Circulate to the CLDR group for comments.

## Blog Post

You need access to Blogger to create a post. The easiest way to do that from the
GDoc is to install the Chrome Add-on "GDocs to Markdown/HTML" by edbacher.

*   In blogger, create a new post and go into HTML mode.
*   In the GDoc, select the body text you want, and pick that add-on. In the
    side panel, hit the button HTML, then copy the resulting HTML into blogger.
*   You might have to add <br> after the </p>s to get the appearance right.
*   To get the image, pick the Image insertion tool.
