# Updating English/Root

Whenever you update English or Root, there is one additional step that needs to
be done for the vetting viewer and tests to work properly.

Update CldrVersion.java to have the newest release in the list.

## **Run GenerateBirth**

The tool is in tools/java/org/unicode/cldr/tool/GenerateBirth.java. It requires
a set of sources from all previous major CLDR release, trunk, and a generation
directory. These three directories must be structured as follows. The tool takes
environment parameters for the second two.

cldr (set with -t <target>, default=CldrUtility.BASE_DIRECTORY, set with
environment variable -DCLDR_DIR)

... common/ ... tools/ java/ (apps such as GenerateBirth are run from here) ...

CldrUtility.ARCHIVE_DIRECTORY (set with environment variable -DARCHIVE=...)
cldr-archive/ cldr-1.1.1/ (content from repos/cldr/tags/release-1-1-1)
cldr-1.2.0/ (content from repos/cldr/tags/release-1-2) cldr-1.3.0/ (content from
repos/cldr/tags/release-1-3) cldr-1.4.1/ (content from
repos/cldr/tags/release-1-4-1) cldr-1.5.1/ (content from
repos/cldr/tags/release-1-5-1) cldr-1.6.1/ (content from
repos/cldr/tags/release-1-6-1) cldr-1.7.2/ (content from
repos/cldr/tags/release-1-7-2) cldr-1.8.1/ (content from
repos/cldr/tags/release-1-8-1) cldr-1.9.1/ (content from
repos/cldr/tags/release-1-9-1) cldr-2.0.1/ (content from
repos/cldr/tags/release-2-0-1) cldr-21.0/ (content from
repos/cldr/tags/release-21)

The archive directory should have the latest version of every major and minor
version (where versions before 21.0 have the major version split across the top
two fields). It will need to match CldrVersion.java.

log (set with -l <log>, default=CldrUtility.UTIL_DATA_DIR, set with CLDR_DIR

You will probably need to modify both CldrVersion.java and ToolConstants.java to
bring them up to date.

Pass an argument for -t to specify the output directory. Takes a few minutes to
run (and make sure you have set Java with enough memory)!

The tool generates (among other things) the following two binary files (among
others) in the output directory specified with -t:

*   **outdated.data**
*   **outdatedEnglish.data**

Replacing the previous versions in
/cldr/tools/java/org/unicode/cldr/util/data/births/. These files are used to
support OutdatedPaths.java.

### Binary File Format

**outdatedEnglish.data** **outdated.data**

**int:size**

long:pathId str:oldValue

long:pathId str:oldValue

...

**$END$**

**str:locale**

**int:size**

long:pathId

long:pathId

...

**str:locale**

**int:size**

long:pathId

long:pathId

…

**$END$** ~50KB ~100KB

In a limited release, the file **SubmissionLocales.java** is set up to allow
just certain locales and paths in those locales.

## Testing

Make sure TestOutdatedPaths.java passes. It may take some modifications, since
it depends on the exact data.

Run TestCheckCLDR and TestBasic with the option **-prop:logKnownIssue=false**
(that option is important!). This checks that the Limited Submission is set up
properly and that SubmissionLocales are correct.

If you run into any problems, look below at debugging.

**Check in the files**

Eg <https://github.com/unicode-org/cldr/pull/243>

## Debugging

It also generates readable log files for double checking. These will be in
{workspace}/cldr-aux/births/<version>/, that is: CLDRPaths.AUX_DIRECTORY +
"births/" + trunkVersion. Examples:
<https://unicode.org/repos/cldr-aux/births/35.0/en.txt>,
<https://unicode.org/repos/cldr-aux/births/35.0/fr.txt>.

Their format is the following (TSV = tab-delimited-values) — to view, it is
probably easier to copy the files into a spreadsheet.

*   English doesn't have the E... values, but is a complete record.
*   Other languages only have lines where the English value is more recently
    changed (younger) than the native’s.
*   So what the first line below says is that French has "bengali" dating back
    to version 1.1.1, while English has "Bangla" dating back to version 30.

LocVersionValuePrevValueEVersionEValueEPrevValuePathfr1.1.1bengali�30BanglaBengali//ldml/localeDisplayNames/languages/language\[@type="bn"\]fr1.1.1galicien�1.4.1GalicianGallegan//ldml/localeDisplayNames/languages/language\[@type="gl"\]fr1.1.1kirghize�24KyrgyzKirghiz//ldml/localeDisplayNames/languages/language\[@type="ky"\]fr1.1.1ndébélé
du Nord�1.3North NdebeleNdebele,
North//ldml/localeDisplayNames/languages/language\[@type="nd"\]fr1.1.1ndébélé du
Sud�1.3South NdebeleNdebele,
South//ldml/localeDisplayNames/languages/language\[@type="nr"\]...fr34exclamation
| point d’exclamation blanc | ponctuationexclamation | point d’exclamation
blanctrunk! | exclamation | mark | outlined | punctuation | white exclamation
markexclamation | mark | outlined | punctuation | white exclamation
mark//ldml/annotations/annotation\[@cp="❕"\]fr34exclamation | point
d’exclamation | ponctuationexclamation | point d’exclamationtrunk! | exclamation
| mark | punctuationexclamation | mark |
punctuation//ldml/annotations/annotation\[@cp="❗"\]fr34cœur | cœur point
d’exclamation | exclamation | ponctuationcœur | cœur point
d’exclamationtrunkexclamation | heart exclamation | mark |
punctuationexclamation | heavy heart exclamation | mark |
punctuation//ldml/annotations/annotation\[@cp="❣"\]fr34couple | deux hommes se
tenant la main | hommes | jumeauxcouple | deux hommes se tenant la main |
jumeauxtrunkcouple | Gemini | man | twins | men | holding hands | zodiaccouple |
Gemini | man | twins | two men holding hands |
zodiac//ldml/annotations/annotation\[@cp="👬"\]fr34couple | deux femmes se tenant
la main | femmes | jumellescouple | deux femmes se tenant la main |
jumellestrunkcouple | hand | holding hands | womencouple | hand | two women
holding hands | woman//ldml/annotations/annotation\[@cp="👭"\]

A value of � indicates that there is no value for that version.
