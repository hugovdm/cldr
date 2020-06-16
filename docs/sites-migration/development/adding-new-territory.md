# Adding a new territory to CLDR

NOTE: It may be helpful to go through the steps in [Updating
Codes](updating-codes/index.md) before proceeding.

Update the following data files:

#### supplemental/

1.  **supplementalData.xml**
    1.  [Update Language Script
        Info](http://cldr.unicode.org/development/updating-codes/update-language-script-info)
        to autogenerate the following elements. If you are splitting off a
        territory, you may have to edit **data/external/other_country_data.txt**
        for tests to pass.
    2.  Sometimes **(when/why?)** running ConvertLanguageData may not make a
        difference in supplementalData, so this step may still have to be
        performed manually. If the territory is split off from an existing
        territory, make sure that the gdp and population for the existing
        territory is reduced accordingly.
            1.  territoryCodes
            2.  territoryInfo
            3.  languageData
        1.  Also do a search for a similar territory code to look for any other
            areas to update. The required information can often be found by
            searching the the territory's official websites, CIA Factbook or
            Wikipedia.
        2.  Manually add relevant territory information to the following
            elements.
            *   `currencyInfo` (Update [Currency
                Codes](updating-codes/update-currency-codes.md) first. If
                updating an unofficial territory, add necessary entries to
                **data/dl_cldr_extensions.xml** for tests to pass.)
            *   `territoryContainment` ([Update Language/Script/Region
                subtags](updating-codes/update-languagescriptregion-subtags.md)
                first. If updating an unofficial territory (e.g. Kosovo), add
                necessary entries to `String[][] extras` in
                **StandardCodes.java** for tests to pass.)
            *   weekData
            *   timeData
2.  **supplementalMetadata.xml:** Add the new territory code to the
    `$territories `variable.
3.  **coverageLevels.xml:** Edit the appropriate `%territory*` coverageVariable
    to make the territory name show up in the Survey Tool for translation (see
    main/en.xml change).
4.  **metaZones.xml:** Add timezone to `metazoneInfo`.
5.  **postalCodeData.xml**
6.  **telephoneCodeData.xml**
7.  **windowsZones.xml:** If the Windows time zones include the new territory,
    then add it to the list.

#### main/

1.  Add **main/<language>_<territory>.xml** for each language used in the
    territory.
2.  **main/en.xml:** Add the name of the territory.

#### collation/

1.  Add the new locales to the `validSubLocales` attribute in the collation
    files of the relevant languages.

Run both ConsoleCheckCLDR and all unit tests (especially TestSupplementalInfo),
and make sure that the new locales and territory name show up in the Survey
Tool.
