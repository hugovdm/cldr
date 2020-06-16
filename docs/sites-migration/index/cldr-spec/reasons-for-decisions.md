# Reasons for Decisions

This page documents reasons why the CLDR Technical Committee has made certain
decisions. It provides a reference that can be cited, for example, when old
issues resurface.

### 1. 2012-02-22 for CLDR 21.0.1 per [#993](http://unicode.org/cldr/trac/ticket/993) (reopened), restore firstDay for IE (Ireland) to be Sunday

*   Before CLDR 1.9 / ICU 4.6, IE was listed (in supplementalData.xml) as using
    Sunday for the first day of the week.
*   As originally filed, [#993](http://unicode.org/cldr/trac/ticket/993)
    requested a change to Monday stating that it was more common. However the
    CLDR TC did not find that there was enough evidence for making a change.
    Also, Séamus Ó Ciardhuáin of NSAI, in a ticket
    [comment](http://unicode.org/cldr/trac/ticket/993#comment:3), mentioned that
    although Monday is sometimes used as the firstDay in a workweek context,
    there are good reasons in history and law for using Sunday; in the latter
    case, a 1937 law defined Sunday as the firstDay, and an NSAI discussion
    reconfirmed this in 2004.
*   [#2052](http://unicode.org/cldr/trac/ticket/2052) claimed that calendars in
    Ireland use Monday as firstDay, and that glibc follows this convention. CLDR
    [checked](http://unicode.org/cldr/trac/ticket/2052#comment:12) some Irish
    transportation schedules; in 5 of 6, the firstDay was Monday. No changes
    were made under this ticket; they were subsumed by the changes discussed in
    the next bullet.
*   Per [#2785](http://unicode.org/cldr/trac/ticket/2785) in CLDR 1.9, the
    behavior of Java (en_IE) and Windows/.NET were checked. Both of these used
    Monday, so IE was removed from the list of countries that used Sunday (thus
    defaulting to Monday, the default firstDay for 001 = the world).
*   Per [#3500](http://unicode.org/cldr/trac/ticket/3500) in CLDR 2.0 there was
    a more
    [comprehensive](https://docs.google.com/spreadsheet/ccc?key=0AjD1-LizLRWldEp6LVBfMXZvZFdSSjU5NVJWUVhWaEE#gid=0)
    investigation of firstDay behavior across locales, comparing to Java and
    Windows. This confirmed Monday as firstDay for Ireland, and it was
    explicitly added to the Monday list.
*   However there is new recent feedback, including feedback from NSAI that
    firstDay should be restored to Sunday. Also, some of the transportation
    schedules [checked](http://unicode.org/cldr/trac/ticket/2052#comment:12)
    under #2052 above as using Monday have
    [changed](http://unicode.org/cldr/trac/ticket/2052#comment:16) to use
    Sunday, and Michael Everson has found several others that also use Sunday:
    [Irish Rail](http://unicode.org/cldr/trac/ticket/2052#comment:15), [Aer
    Lingus](http://unicode.org/cldr/trac/ticket/2052#comment:17), etc.
*   NSAI intends to lobby to have glibc, Windows, and Java use Sunday as the
    firstDay for Ireland.

Per CLDR discussion 2011-02-22, we will change firstDay back to Sunday for IE
