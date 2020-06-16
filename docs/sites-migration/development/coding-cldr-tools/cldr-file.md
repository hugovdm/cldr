# CLDR File

[TOC]

## Introduction

CLDR File is a workhorse for CLDR tools. It has grown and changed over the
years, without a serious rearchitecture, so there are oddities in its usage and
construction that we'll try to describe here.

The CLDR File is basically a representation of an XML file as a set of <key,
value> pairs, where the key is a path, and the value is the element value at the
path. This structure allows the XML file to use inheritance, and allows it to be
modified without worrying about the exact structure. When a <key,value> pair is
added, the CLDR file will make sure that the written form of the resulting XML
file is syntactically correct.

Because CLDR File incorporates inheritance, and because the data source may be a
database and not just in-memory storage, the actual contents are in a separate
object called XMLSource. That object has all of the inheritance logic in it, but
it is closely coupled to the CLDR File.

The structure is a bit more complicated than just a <path,value> pair:

1.  For inheritance, the path removes attributes that don't count for the
    purposes of inheritance. So there is a separate mapping from the path to the
    "full" path, with those attributes. These are only used where necessary.
    This information is in CLDRFile.isDistinguishing.
2.  There is a separate mapping for comments. This indicates where a comment
    attaches to an element (before, at, or after). If the CLDR File has been
    modified to remove the path, then the comment is still printed, but in a
    manufactured location.
3.  As a CLDR File is input, certain changes may be made to the structure,
    including the addition of attributes in order to get the ordering correct.
4.  A hack is used for inheritance to get the "count" values to come out right.
    (We should clean this up).
5.  A by-product of the <key,value> pair nature is that no CLDR XML file can
    have mixed content: the content of every element is either a value, or a
    sequence of elements.

Because of these complications, when a new element or attribute is added to the
DTD, adjustments **have to be made** to the code in CLDRFile and other places.
(The longer-range plan is to read these out of the supplemental metadata
instead.) For details, see [Updating DTDs](../updating-dtds/index.md).

## Input

When a file is read, the orderedElements value is used to determine which
elements are not reordered or inherited. Those elements get an artificial
attribute "_q" with an increasing number as they are read.

## Output

The write method writes out an XML file. The ordering is determined by
LDMLComparator, which uses the elementOrdering, attributeOrdering, and
valueOrdering. These are MapComparators, which provide an ordering based upon
specific lists of elements. Those lists are derived programmatically from the
DTD, using a tool. \[TBD add link\]. The value comparison is further tweeked
according to the element and attribute, so that, for example, the days of the
week come out in the right order. See getAttributeValueComparator.

Certain attributes are suppressed. These are in defaultSuppressionMap.

A MapComparator behaves in the following way.

1.  If both items are in the ordered list, it returns the ordering according to
    that list. Else if exactly one is, it comes first (TBD check this).
2.  If both items are numeric (all digits), then the ordering is the normal
    numeric order. Else if exactly one is, it comes first (TBD check this.)
3.  Else return the "natural" comparison: return ((Comparable)a).compareTo(b);

## Usage

Normally you iterate through CLDR File with interator(). This returns the paths
in random (hashed) order. There are, however, some options that let you iterator
through a subset of the paths: only paths that match a prefix string, or those
that only match a regular expression. You can also use a comparator (you should
use CLDRFile.ldmlComparator) to change the order of iteration. Example:

for (Iterator it = cldrFile.iterator("", CLDRFile.ldmlComparator);
it.hasNext();)

String path = (String) it.next();

String value = cldrFile.getStringValue(path);

String fullpath = cldrFile.getFullXPath(path);

The fullpath has the nondistinguished attributes added.
