# Updating Survey Tool

[TOC]

### Supplemental Data/structure

1.  Make the change to a supplemental file and/or DTD. (See XXX for details.)
2.  Run TestSupplementalInfo (if you added new structure, add a test there).

### Testing Code

1.  Go to <http://kwanyin.unicode.org/cldr-build/>
2.  Click **update code**
3.  Wait until done (<1min)
4.  Go to <http://kwanyin.unicode.org:8080/cldr-apps/survey>
5.  Test & repeat above until it looks good.

### Updating Survey Tool Code

1.  Go to <http://unicode.org/cldr/apps/survey?dump=combining&action=specialmsg>
2.  Change the message to "The server will be going down soon for maintenance:
    please save your work."
    ( Note: See [cldr-properties](cldr-properties/index.md) for how to set this
    message permanently.)
3.  Set the timer to, say, 300.
4.  Click \[set\]
5.  Wait until the timer runs out.
6.  Go back to <http://kwanyin.unicode.org/cldr-build/>
7.  Click on ==Update Survey Tool **code**...== to update the code.
8.  Wait until ST updates.
9.  Do a quick sanity check (open a locale, click on section, click on Vetting
    Viewer.

### Updating Survey Tool Data

1.  Do "Updating Survey Tool Code"
2.  Wait until done (<1min)
3.  Click **Update DATA on [unicode.org](http://unicode.org/) (login and do Easy
    Data Update as admin afterwards)**
4.  Wait until done (<1min)
5.  Go back to
    <http://unicode.org/cldr/apps/survey?dump=combining&action=specialmsg>
6.  Click **Easy Data Update**
7.  Wait quite a while. (? 10min?)
8.  Go to <http://unicode.org/cldr/apps/survey>
9.  Test again.
