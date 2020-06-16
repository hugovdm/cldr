# Macrolanguages

In supplementalMetadata.xml is a list of macrolanguages. Each line must specific
a mapping from **the predominant** encompassed language to the macrolanguage.
The macro language mappings are on:

[
http://www.sil.org/iso639-3/macrolanguages.asp](http://www.sil.org/iso639-3/macrolanguages.asp)
For example, Bontok macrolanguage (bnc) encompasses a bunch of others:

[                       bnc](javascript:void(0);)
Bontok                                          [
ebk](javascript:void(0);)                                               Eastern
Bontok
[                       lbk](javascript:void(0);)
Central Bontok
[                       obk](javascript:void(0);)
Southern Bontok
[                       rbk](javascript:void(0);)
Northern Bontok
[                       vbk](javascript:void(0);)
Southwestern Bontok

Be sure to also change the comment if making a change, otherwise it will be
misleading.

In the above example case, the "most predominant" form is "lbk" (Central Bontok)
with the largest population. The resulting line in the XML file would be:

<languageAlias type="lbk" replacement="bnc"/> <!-- Central Bontok => Bontok -->
