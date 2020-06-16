# DisplayAndInputProcessor

[TOC]

There are a few ways to change CLDR data. One of these is
DisplayAndInputProcessor.java. The advantage of this method is that it will be
run ***whenever*** users enter data in the Survey Tool — and in the final
processing of all CLDR data.

So, for example, spaces in number formats can be always changed to non-breaking
spaces (U+00A0).

The exact processing of values can, and usually does, depend on the particular
field (based on the path and even the locale). Because these are always run,
with no choice of options, they are not appropriate unless the changes
***always*** want to be made.

## To make the changes

Go into DisplayAndInputProcessor.java and look how the changes are handled
there. The main methods are:

*   processForDisplay - used to display in the ST
*   processForInput - used to normalize data on input

For example, the following is found in processForInput

// Normalize ellipsis data.

**if** (path.startsWith("//ldml/characters/ellipsis")) {

value = value.replace("...", "…");

}

## Coordinating Display and Input

You can make changes in the display that are reversed in the input. For example,
you could replace {0} by ⓪, {1} by ①, and so on in the display, then reverse
that change on input.

## Testing changes

Add test for your particular changes to TestDisplayAndInputProcessor.java. Run
that, then run TestAll to make sure you don't affect other processing.

Next, you can run CLDRModify with the -fp option (see [CLDRModify
Passes](index.md)). You can limit this to a few locales initially using the flag
XX. Do a diff on the files to make sure that the changes you see are the changes
you expected. Once you have iterated and are satisfied, run them on all locales,
and do a spot-check on differences to make sure that everything is ok.

Then check in your changes to DisplayAndInputProcessor, to
TestDisplayAndInputProcessor, and to the locales.
