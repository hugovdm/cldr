# Updating Population, GDP, Literacy

**Updated 2016-09-02 by Davis**

Instructions are based on FIrefox browser.

## Load the World DataBank

## The World DataBank is at (<http://databank.worldbank.org/data/views/variableselection/selectvariables.aspx?source=world-development-indicators>). Unfortunately, they keep changing the link. If the page has been moved, try to get to it by doing the following. Each of the links are what currently works, but that again may change.

1.  Go to <http://worldbank.org>
2.  Click "Data" at top (<http://data.worldbank.org/>)
3.  Click "Data Catalog" (<http://datacatalog.worldbank.org/>)
4.  Click "World Development Indicators"
    (<http://data.worldbank.org/data-catalog/world-development-indicators>)
5.  Click on the blue "DATABANK" link in the "". It should be at or near the
    top.
    (<http://databank.worldbank.org/data/reports.aspx?source=world-development-indicators>)

Once you are there, generate a file by using the following steps. There are 3
collapsible sections, "COUNTRIES", "SERIES", and "TIME"

*   Countries

    *   Expand the "Countries" section, click the "Countries" tab, and then
        click the "Select All" button on the left. You do NOT want the
        aggregates here, just the countries. There were 217 countries on the
        list when these instructions were written; if substantially more than
        that, you may have mistakenly included aggregates.

*   Series
    *   Expand the "Series" section.
    *   Select "Population, total"
    *   Select "GNI, PPP (current international $)"

*   Time
    *   Select all years starting at 2000 up to the latest available year. The
        latest as of this writing was "2015". Be careful here, because sometimes
        it will list a year as being available, but there will be no real data
        there, which messes up our tooling. ( Currently it claims that there is
        2016 data there, but there is none. )
        *   **If the latest year is greater than the latest year** in the
            current
            tools/java/org/unicode/cldr/util/data/external/workd_bank.csv, then
            add the new one(s) to the WBLine enum in
            **org/unicode/cldr/tool/AddPopulationData.java** .

*   Click the "Download Options" link in the upper right.
    *   A small "Download options" box will appear.
    *   Select "CSV" and click "Download".
    *   Instruct your browser to the save the file.
*   You will receive a ZIP file named
    "Data_Extract_From_World_Development_Indicators".
    *   Unpack this zip file. It will contain two files.
    *   The larger file (about 100kb) contains the actual data we are interested
        in. The file name should be something like
        56cb30da-d092-46a5-bbb3-cbc54aafa279_Data.csv
    *   The smaller file is just a field definitions file that we don't care
        about.

*   Verify that the data file is of the form:
    *   Country Name,Country Code,Series Name,Series Code,2000 \[YR2000\],2001
        \[YR2001\],2004 \[YR2004\],...
    *   Afghanistan,AFG,"Population,
        total",SP.POP.TOTL,19701940,20531160,23499850,24399948,25183615,...
    *   Afghanistan,AFG,"GNI, PPP (current international
        $)",NY.GNP.MKTP.PP.CD,..,..,22134851020.6294,25406550418.3726,27761871367.4836,32316545463.8146,...
    *   Albania,ALB,"Population,
        total",SP.POP.TOTL,3089027,3060173,3026939,3011487,2992547,2970017,...
    *   ...

*   Rename it to world_bank_data.csv and and save in
    **org/uniocde/cldr/util/data/external/**
*   Diff the old version vs. the current.
*   If the format changes, you'll have to modify AddPopulationData.WBLine to
    have the right order and contents. Often this is just adding an extra year
    field.

## Load UN Literacy Data

1.  Goto <http://unstats.un.org/unsd/demographic/products/socind/default.htm>
2.  Click on "Education"
3.  Click in "Table 4a - Literacy"
4.  Download data - save as temporary file
5.  Open in Excel or OpenOffice - save as data/external/un_literacy.csv (Windows
    Comma Separated)
    1.  If it has multiple sheets, you want the one that says "Data", and looks
        like:
    2.  Table 4a. Literacy
    3.  Last update: December 2012
    4.  Country or area Year            Adult (15+) literacy rate       Youth
        (15-24) literacy rate
    5.  Total           Men             Women           Total            Men
        Women
    6.  Albania 2008            96              97              95
        99              99              99
6.  Diff the old version vs. the current.
7.  If the format changes, you'll have to modify the loadUnLiteracy() method in
    **org/unicode/cldr/tool/AddPopulationData.java**

## Load CIA Factbook

1.  All files are saved in **org/unicode/cldr/util/data/external/**
2.  Goto:
    <https://www.cia.gov/library/publications/the-world-factbook/index.html>
3.  Goto the "References" tab, and click on "Guide to Country Comparisons"
4.  Expand "People and Society" and click on "Population" -
    1.  Right Click on DownloadData, Save Link As... call it
    2.  **factbook_population.txt**
5.  Back up a page, then Expand "Economy" and click on "GDP (purchasing power
    parity)"
    1.  Right Click on DownloadData, Save Link As... call it
    2.  **factbook_gdp_ppp.txt**
6.  **No longer works, so we need to revise program - They are still publishing updates to the data at this page, we just need to write some code to put the data into a form we can use, see <http://unicode.org/cldr/trac/ticket/9756#comment:4>**Literacy -
    1.  <https://www.cia.gov/library/publications/the-world-factbook/fields/2103.html>
    2.  Right Click on "Download Data", Save Link As... Call it
    3.  **factbook_literacy.txt**
7.  Diff the old version vs. the current.
8.  If the format changes, you'll have to modify the loadFactbookLiteracy())
    method in **org/unicode/cldr/tool/AddPopulationData.java**

## Convert the data

1.  If you saw any different country names above, you'll need to edit
    external/alternate_country_names.txt to add them.
    1.  For example, we needed to add Czechia in 2016.
2.  If two-letter non-countries are added, then you'll need to adjust
    StandardCodes.isCountry.
3.  Run "AddPopulationData *-DADD_POP*=**true"** and look for errors.
4.  Once everything looks ok, check everything in to SVN.
5.  Once done, then run the ConvertLanguageData tool as on [Update Language
    Script Info](update-language-script-info/index.md)
