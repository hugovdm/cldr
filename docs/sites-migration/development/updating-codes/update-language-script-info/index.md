# Update Language Script Info

## Main

1.  Rick should have checked in spreadsheets in
    {cldrdata}\\tools\\java\\org\\unicode\\cldr\\util\\data, with names of the
    form:
    1.  **country_language_population_raw.txt**
    2.  **language_script_raw.txt**
    3.  For a descriptions of the contents, see [Language Script
        Guidelines](language-script-description.md)
    4.  Do not edit the above files with a plain text editor; they are
        tab-delimited UTF-8 with many fields and should be imported/edited with
        a spreadsheet editor. Rick uses Excel, but Google sheets should also
        work fine.
2.  The world bank, un, and factbook data should be updated as per [Updating
    Population, GDP, Literacy](../updating-from-world-bank.md)
3.  Note that there is an auxiliary file
    **util/data/external/other_country_data.txt**, which contains data that
    supplements that. If there are errors below because the country population
    is less than the language population, then that file may need updating.
4.  Run the tool ConvertLanguageData.
    1.  *-DADD_POP*=**true**; for error messages.
    2.  If there are any different country names, you'll get an error: edit
        external/alternate_country_names.txt to add them.
    3.  Look for failures in the language vs script data, following the line:
        *   **Problems in language_script_raw.txt**
    4.  Look for Territory Language data, following the line:
        *   **Possible Failures** ...
            *   In Basic Data but not Population > 20%
            *   and the reverse.
    5.  Look for general problems, following the line:
        *   **Failures in Output.**
        *   It will also warn if a country doesn't have an official or de facto
            official language.
    6.  Send all the error reports back to Rick. Work until resolved.
5.  It creates files:
    *   {generated}supplemental/supplementalData.xml
6.  ***Carefully*** diff against the corresponding
    {cldrdata}/common/supplemental/ file.
7.  If all looks well, copy over.
8.  Then run QuickCheck to verify that the DTD is in order, and check in.

## Update the supplementalData.xml <territoryContainment>

1.  *Note: should automate this! (JCE: These instructions are too fragile to be useful. "Copy the table" results will vary widely depending on which browser you use!)*
2.  For the basic containment, go to
    <http://unstats.un.org/unsd/methods/m49/m49chang.htm>. Check if anything has
    changed.
3.  Then go to <http://unstats.un.org/unsd/methods/m49/m49regin.htm>, copy the
    table, and paste into **util/data/external/m49_raw.txt**. Diff with old
4.  For the UN, go to <http://www.un.org/en/member-states/index.html>. Copy the
    table, and paste into **util/data/external/un_member_states_raw.txt**. Diff
    with old.
5.  For the EU, do the same with
    <https://europa.eu/european-union/about-eu/countries/member-countries_en>,
    into **util/data/external/eu_member_states_raw.txt**
6.  For the EZ, do the same with
    <http://ec.europa.eu/economy_finance/euro/adoption/euro_area/index_en.htm>,
    into **util/data/external/ez_member_states_raw.txt**
7.  If there are changes, update <territoryContainment>
