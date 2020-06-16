# Testing Keyboards

The main directories in the keyboards/ directory are:

*   [android/](http://www.unicode.org/repos/cldr/trunk/keyboards/android/)
*   [chromeos/](http://www.unicode.org/repos/cldr/trunk/keyboards/chromeos/)
*   [osx/](http://www.unicode.org/repos/cldr/trunk/keyboards/osx/)
*   [und/](http://www.unicode.org/repos/cldr/trunk/keyboards/und/)
*   [windows/](http://www.unicode.org/repos/cldr/trunk/keyboards/windows/)

All but /und/ are designed to reflect what is available on a particular
platform, and are derived mechanically. Changes to those need to be requested of
the platform vendors. Any keyboard files that are intended for a given platform,
but are not “official” on that plaform will go into /und/.

Keyboard data that is not supported on a given platform, but intended for use
with that platform, may be added to the directory /und/. For example, there
could be a file /und/lt-t-k0-chromeos.xml, where the data is intended for use
with ChromeOS, but does not reflect data that is distributed as part of a
standard ChromeOS release.

We have found that most submissions have data errors which prevent our adding
the keyboard files, and we don't have the resources to do a back-and-forth to
fix them manually. We are thus dependent on the submitter running the tests,
which means setting up CLDR locally so that the tooling can be run.

So in the ticket, the submitter must indicate that:

1.  the new keyboards are intended to go into /und/, and
2.  they have passed those tests.

We intend to develop an online tool to make this easier, but that is not yet in
place.

## Running the test

If you don't have CLDR tools set up, the easiest way is to start with [Eclipse
Setup](eclipse-setup/index.md).

Once it is all set up, add the new keyboard under und/. Make sure that the id
for the keyboard is correct according to [bcp47 with extension
-t-](http://www.unicode.org/reports/tr35/#Locale_Extension_Key_and_Type_Data),
and matches the file name, and that the other lines in the file are well-defined
according to [LDML
Keyboards](http://www.unicode.org/reports/tr35/tr35-keyboards.html). The
keyboard id *must* be different than all of the platform keyboard ids, so it
might be something like “lt-t-k0-osx**-xvar**”.

Run ShowKeyboards.java, which reads all the keyboard files and writes out the
charts. Use the option ? to see the options you can supply. (For example, you
can supply a regex to filter the ids to just the added keyboard.)

Fix any errors in the new XML file, and iterate until the tool runs without
errors. Examine the resulting charts for the new keyboard, and make sure they
match the intent of the file.
