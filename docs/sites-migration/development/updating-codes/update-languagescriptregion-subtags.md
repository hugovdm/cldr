# Update Language/Script/Region Subtags

### Updated 2015-08-07 by J. C. Emmons

### This updates language codes, script codes, and territory codes.

*   First get the latest ISO 639-3 from
    <http://www-01.sil.org/iso639-3/download.asp>
    *   Download the zip file containing the UTF-8 tables, it will have a name
        like
        [iso-639-3_Code_Tables_20150505.zip](http://www-01.sil.org/iso639-3/iso-639-3_Code_Tables_20150505.zip)
    *   Unpack the zip file and rename the 4 files to match the following:
        *   {cldrdata}tools\\java\\org\\unicode\\cldr\\util\\data\\iso-639-3.tab
        *   {cldrdata}\\tools\\java\\org\\unicode\\cldr\\util\\data\\iso-639-3_Name_Index.tab
        *   {cldrdata}\\tools\\java\\org\\unicode\\cldr\\util\\data\\iso-639-3-macrolanguages.tab
        *   {cldrdata}\\tools\\java\\org\\unicode\\cldr\\util\\data\\iso-639-3_Retirements.tab
    *   Take the **latest** version number of any of the files (like
        iso-639-3_**20070615**.tab), and paste into
        *   {cldrdata}\\tools\\java\\org\\unicode\\cldr\\util\\data\\iso-639-3-version.tab
*   Go to <http://www.iana.org/assignments/language-subtag-registry>
    *   (you can set up a watch for changes in this page with
        <http://www.watchthatpage.com> )
    *   Save as
        {cldrdata}\\tools\\java\\org\\unicode\\cldr\\util\\data\\language-subtag-registry
*   Go to http://data.iana.org/TLD/
    *   Right-click on
        [tlds-alpha-by-domain.txt](http://data.iana.org/TLD/tlds-alpha-by-domain.txt)
        save as
    *   {cldrdata}\\tools\\java\\org\\unicode\\cldr\\util\\data\\[tlds-alpha-by-domain.txt](http://data.iana.org/TLD/tlds-alpha-by-domain.txt)
*   If using Eclipse, refresh the files
*   Diff each with the old copy (via "svn diff" or Eclipse "compare with base
    from working copy") to check for consistency
    *   Certain of the steps below require that you note certain differences.
    *   Check if there is a new macrolanguage (marked with M in the second
        column of the iso-639-3.tab file). (Should automate this, but there
        typically aren't that many new/changed entries).
    *   Check if ISO has done something destabilizing with codes: you need to
        handle it specially
    *   ...
*   Do validity checks and regenerate: for details see
    [Validity](update-validity-xml.md)
    *   You'll have to do this again in [Updating Subdivision
        Codes](updating-subdivision-codes.md).
*   Edit common/main/en.xml to add any new names, based on the Descriptions in
    the registry file.
    *   *You only need to add new languages and scripts that we add to
        supplementalMetaData.*
    *   But you need all territories.
    *   Any new macrolanguages need a language alias.
    *   Diff for sanity check
*   If the code becomes deprecated, then add to supplementalMetadata under
    <alias>
    *   If there is a single replacement add it.
    *   Territories can have multiple replacements. Put them in population
        order.
*   There are a few territories that don't yet have a top level domain (TLD)
    assigned, such as "BQ" or "SS".
    *   If there are new ones added in tlds-alpha-by-domain.txt for a territory
        already in CLDR, update
        {cldrdata}\\tools\\java\\org\\unicode\\cldr\\util\\data\\territory_codes.txt
        with the new TLD (usually the same as the country code.

*   For new territories (regions) // TODO: automate this more
    *   Add to the territoryContainment in supplementalData.xml
        *   The data for that is at the UN site:
            <http://unstats.un.org/unsd/methods/m49/m49regin.htm>
        *   With data from the EU at
            <http://europa.eu/abc/european_countries/index_en.htm>
    *   Add to territory_codes.txt
        *   Use the UN mapping above for the 3letter and 3number codes.
        *   FIPS is a withdrawn standard as of 2008, so any new territories won't have a FIPS10 code.
        *   Look at tlds-alpha-by-domain.txt to see if the new territory has a
            TLD assigned yet.
        *   rerun CountItems above.
    *   Add metazone mappings as needed. (Usually John - requires research)
    *   Add the country/lang/population data (Usually Rick - requires research)
    *   Add the currency data (Usually John - requires research)
    *   ~~Update util/data/territory_codes.txt~~
        *   ~~This step will be different once the data is moved into
            SupplementalData.xml~~
        *   ~~Todo: fix GenerateEnums around
            Utility.getUTF8Data("territory_codes.txt");~~
*   Then run GenerateEnums.java, and make sure it completes with no exceptions.
    Fix any necessary results.
    *   Missing alpha3 for: xx, or "In RFC 4646 but not in CLDR: \[EA, EZ, IC,
        UN\]"
        *   Ignore if it is {EA, EZ, IC, UN} Otherwise means you needed to do
            "For new territories" above
    *   Collision with: xx
        *   Ignore if it is {{MM, BU, 104}, {TP, TL, 626}, {YU, CS, 891}, {ZR,
            CD, 180}}
    *   Not in World but in CLDR: \[002, 003, 005, 009, 011, 013, 014, 015,
        017... Ignore 3-digit coes
    *   (should have exception lists in tool for the Ignore's above)
*   Run ConsoleCheckCLDR -f en -z FINAL_TESTING -e
    *   If you missed any codes, you will get error message: "Unexpected
        Attribute Value"
*   Run all the unit tests.
    *   If you get a failure in LikelySubtagsTest because of a new region, you
        can hack around it with something like:
        *   <likelySubtag from="und_202" to="en_Latn_NG"/>
        *   <!-- hack until rebuilt -->
    *   You may also have to fix the coverageLevels.txt file for an error like:
        *   Error: (TestCoverageLevel.java:604) Comprehensive & no exception for
            path =>
            //ldml/localeDisplayNames/territories/territory\[@type="202"\]
