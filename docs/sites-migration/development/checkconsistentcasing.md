# Updating CheckConsistentCasing

To update the casing information for a locale, run
org.unicode.cldr.test.CasingInfo -l <locale_regex>. This will update the
relevant casing files in common/casing.

The complete list of casing types is in CheckConsistent.casing.typeNames and
their corresponding XPaths are in pathToBucket.
