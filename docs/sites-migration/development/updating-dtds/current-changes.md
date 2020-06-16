# current changes

John: please add this page to the BRS. The first step should be to find the
diffs and record here. This step should come early on the BRS page. Once we have
people, we can file bugs on each change.
All, the DTD snippets should appear in the spec in the appropriate place. There
is also a style we use for them.
========================

## ldml

========================

### **Peter (already covered by 1949)**

<!ELEMENT gmtZeroFormat ( #PCDATA ) >
<!ATTLIST gmtZeroFormat alt CDATA #IMPLIED >
<!ATTLIST gmtZeroFormat draft ( approved | contributed | provisional |
unconfirmed | true | false ) #IMPLIED > <!-- true and false are deprecated. -->
<!ATTLIST gmtZeroFormat references CDATA #IMPLIED >

### John

<!ELEMENT defaultNumberingSystem ( #PCDATA ) >
<!ATTLIST defaultNumberingSystem references CDATA #IMPLIED >
<!ATTLIST defaultNumberingSystem draft ( approved | contributed | provisional |
unconfirmed | true | false ) #IMPLIED > <!-- true and false are deprecated. -->
<!ATTLIST defaultNumberingSystem alt CDATA #IMPLIED >
<!ATTLIST pattern numbers CDATA #IMPLIED >

### John (**2199** done)

<!ELEMENT rbnf ( alias | rulesetGrouping\*) >
<!ELEMENT rulesetGrouping ( alias | ruleset\*) >
<!ATTLIST rulesetGrouping type NMTOKEN #REQUIRED>
<!ATTLIST rulesetGrouping draft ( approved | contributed | provisional |
unconfirmed | true | false ) #IMPLIED ><!-- true and false are deprecated. -->
<!ELEMENT ruleset ( alias | rbnfrule\*) >
<!ATTLIST ruleset type NMTOKEN #REQUIRED>
<!ATTLIST ruleset access ( public | private ) #IMPLIED >
<!ATTLIST ruleset draft ( approved | contributed | provisional | unconfirmed |
true | false ) #IMPLIED ><!-- true and false are deprecated. -->
<!ELEMENT rbnfrule ( #PCDATA ) >
<!ATTLIST rbnfrule value CDATA #REQUIRED >
<!ATTLIST rbnfrule radix CDATA #IMPLIED >
<!ATTLIST rbnfrule decexp CDATA #IMPLIED >
<!ATTLIST rbnfrule draft ( approved | contributed | provisional | unconfirmed |
true | false ) #IMPLIED ><!-- true and false are deprecated. -->
========================

## supplemental

========================

### John

<!ATTLIST currency tender ( true | false ) #IMPLIED >

### Mark (2200 done)

<!ELEMENT postalCodeData (postCodeRegex\*) >
<!ELEMENT postCodeRegex (#PCDATA) >
<!ATTLIST postCodeRegex territoryId NMTOKEN #REQUIRED>
<!ATTLIST postCodeRegex draft ( approved | contributed | provisional |
unconfirmed | true | false ) #IMPLIED > <!-- true and false are deprecated. -->

### Yoshito (2201 done)

<!ELEMENT calendarPreferenceData ( calendarPreference\* ) >
<!ELEMENT calendarPreference EMPTY >
<!ATTLIST calendarPreference territories NMTOKENS #REQUIRED >
<!ATTLIST calendarPreference ordering NMTOKENS #REQUIRED >
<!ATTLIST calendar territories NMTOKENS #IMPLIED > <!-- territories are
deprectead. use ordering attribute in calendarPreference element instead. -->

### John (**2199** done)

<!ELEMENT numberingSystems ( numberingSystem\* ) >
<!ELEMENT numberingSystem EMPTY >
<!ATTLIST numberingSystem id NMTOKEN #REQUIRED >
<!ATTLIST numberingSystem type ( numeric | algorithmic ) #REQUIRED >
<!ATTLIST numberingSystem radix NMTOKEN #IMPLIED >
<!ATTLIST numberingSystem digits CDATA #IMPLIED >
<!ATTLIST numberingSystem rules CDATA #IMPLIED >

### Yoshito (1730 - done in Appendix C / #1730 also require Section 3.2 to be updated)

<!ELEMENT bcp47KeywordMappings ( mapKeys?, mapTypes\* ) >
<!ELEMENT mapKeys ( keyMap\* ) >
<!ELEMENT keyMap EMPTY >
<!ATTLIST keyMap type NMTOKEN #REQUIRED >
<!ATTLIST keyMap bcp47 NMTOKEN #REQUIRED >
<!ELEMENT mapTypes ( typeMap\* ) >
<!ATTLIST mapTypes type NMTOKEN #REQUIRED >
<!ELEMENT typeMap EMPTY >
<!ATTLIST typeMap type CDATA #REQUIRED >
<!ATTLIST typeMap bcp47 NMTOKEN #REQUIRED >
=====
Changes (running CLDRCompare, and using a spreadsheet to summarize results)
New Deleted Same Differ Total New% Deleted% Same% Differ% TOTAL 40475 14567
135083 6219 196344 20.6% 7.4% 68.8% 3.2%
collation 66 67 13846 3 13982 0.5% 0.5% 99.0% 0.0%
main 28491 10406 104857 5115 148869 19.1% 7.0% 70.4% 3.4%
rbnf 7422 0 0 0 7422 100.0% 0.0% 0.0% 0.0%
segments 12 0 239 2 253 4.7% 0.0% 94.5% 0.8%
supplemental 3517 3132 2811 6 9466 37.2% 33.1% 29.7% 0.1%
transforms 967 962 13330 1093 16352 5.9% 5.9% 81.5% 6.7%
