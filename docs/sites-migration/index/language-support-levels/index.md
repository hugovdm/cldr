# Language Support Levels

Programs and devices can offer different levels of support for different
languages. It is useful to distinguish three of these: *basic language support*,
*content language support*, and *UI language support*.

## Basic language support

The most basic language support requires Unicode characters for writing that
language, the Unicode properties and algorithms for those characters that let
them work on computers and phones (such as line-wrapping), the fonts used to
display those characters, and the keyboard layouts needed to enter those
characters.

That is, the text is interchangeable across devices, it displays as expected on
any device (given fonts), and users can enter and edit text in that language.

## Content language support

For content language support, the user sees correct processing for that
language, with sorting, matching, display and entry of dates, times, numbers,
currencies, and so on. This requires data and algorithms that support these
features, so that a phone or other device knows to display a date as “Freitag,
13. Januar 2012” or “Παρασκευή, 13 Ιανουαρίου 2012”.

## UI language support

For UI-language support, the language is also supported in the user interface of
an application, web page, or OS: All of the menus, dialogs, help-text, and so on
are in the user’s language. The user doesn’t need to know another language in
order to use the application, web page, or OS.

Of course, more sophisticated programs will further layer on top of UI or
content language support to offer capabilities that depend on language: complex
searching algorithms will identify entities in the text, and allow for matching
that takes into account linguistic synonyms and inflections; text-to-speech and
speech-to-text capabilities allow the user to easily interact with a device, and
so on. These tend to require very sophisticated machine-learning models,
typically based on massive amounts of data.

## In practice

Much of the world is multilingual, and people are often fluent enough in a
second language to be able to use that as their UI language. But they still want
and need to be able to use their language as a content language. Take Yoruba,
for example, with ca. 30 million speakers. A Yoruba speaker may be able to use
English as their UI language, but still needs to be able to write emails in
Yoruba, compose documents in Yoruba, and create a spreadsheet in Yoruba. To help
with language preservation, content language support on digital devices is an
important step above basic language support.

The Unicode Consortium enables vendors to support additional content languages
by providing the characters those languages need, the properties and algorithms
for those characters that let them work on computers and phones (line break,
...), and core linguistic support (sorting, matching; keyboard layouts;
entering/displaying dates, times, numbers, currencies, measurements, country
names,…). The consortium doesn't supply fonts, but those are available from
other sources, such as [Google's Noto fonts
project](https://www.google.com/get/noto/) (free, under the *open font
license*).

The consortium also offers some support for *UI language* support in CLDR and
ICU, but most of the work necessary to support a given language as a UI language
depends on the app or OS provider doing the necessary translations.

## Example: Cherokee

For basic language support, characters for Cherokee had to be added to Unicode,
since it doesn’t use the Latin characters (A, B, C, ... ). The Unicode
properties had to be supplied, so that the standard Unicode algorithms would
work for for text comparison, line-wrap, word selection, and so on. Fonts and
keyboard layouts for Cherokee are available, but might require an additional
step for installation if not already on the OS. The content language support for
dates, times, and other features are provided for in CLDR.

Developers can produce apps that support Cherokee as a content language using
the Unicode ICU libraries. It supplies them with the code to handle the
necessary Unicode characters, properties and algorithms, and the CLDR
content-language data.

With somewhat more work, developers can support Cherokee as a UI language, with
translated menus, dialogs, help content, and so on. The number of products with
UI support for smaller languages like Cherokee is often quite limited, however,
due to the expense of the translation and maintenance.

Systems that support the most up-to-date Unicode ICU libraries (like Android or
the Mac) should see Cherokee as a choice among languages. It is not typically a
UI language for the OS, meaning the system isn't translated into it. So in
practice a user must also select an alternative language such as English that
will appear in the UI. For example, on a Mac someone can pick a Cherokee
keyboard, and type in GMail the Cherokee characters:

### Language selection UI

Below are examples of selecting Cherokee on different systems. (Cherokee in
Cherokee looks like "CWY", and is midway down on each.)

Android Macintosh Windows
