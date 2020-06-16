# Metazone-Reform

We do not have good coverage for metazones. I've been trying to determine the
set of metazones that need to be translated as the highest priority. In so
doing, this involves decideing where we really need metazones, and where we
don't. This is for use with the XMB translation, but it has overlap with the
other coverage work we're doing.

Here are my thoughts.

1.  The country-name-style works pretty well as a fallback, and doesn't need
    extra strings translated (11:00 Cuba Time)
2.  If a country has a single timezone\*, use the fallback. (\*\*We can remove
    existing metazones for these cases)
3.  Some countries have a small population. Skip them, since the fallback is
    sufficient.
4.  Some countries, practically speaking, have a single zone with some outlying
    regions of small population. Skip them, since the fallback is sufficient.
5.  This gives the following countries: AR, AU, BR, CA, ID, KZ, MN, RU, US
6.  Translate the metazones with golden zones in those countries. That gives 55
    metazones.
7.  Of those:
    1.  If the golden zone has daylight savings\*, then translate 3 strings:
        **generic**, **standard**, and **daylight**
    2.  Otherwise, translate 1 string: **generic**
    3.  This would involve some rework of existing data.

The \* is because we don't care about historic differences. I'm recommending
using the period 2010 to 2015, because that is where we care most about it.

The current breakdown according to this is in the following spreadsheet:
<http://goo.gl/14XR9>

---

I ran into some oddities along the way.

1.  I stumbled with the function myZone.useDaylightTime. It **doesn't** mean
    "inDaylightTime=true for some date". Nor does it mean "inDaylightTime=true
    at the moment". What it appears to mean is that the current rules in effect
    allow for daylight time, which is sort-of useless; it doesn't tell us much
    in practical terms.
2.  Antarctica/South_Pole is missing a metazone. We should have a release test
    to make sure that all the metazone data is consistent.
3.  I think we should change some of the metazones; I think we should rework as
    follows, to reflect the best state of affairs after 1983:

**Proposal:**

Alaska - delete

Hawaii_Aleutian => Hawaii

Alaska_Hawaii => Alaska

\[JCE\] I don't think this is correct. The current ones ( in modern day usage )
are "Alaska" and "Hawaii_Aleutian". The "Alaska_Hawaii" one is the old one that
was in effect prior to 1983.

We don't actually need the old "Alaska", since it wasn't in use before 1983.
"Hawaii-Aleutian (Standard) Time" is used, but far less than "Hawaii (Standard)

Time".

Here is the data:

**Region Metazone Golden_Zone**

US      Alaska  America/Juneau

US      Alaska_Hawaii   America/Anchorage

US      Hawaii_Aleutian Pacific/Honolulu

America/Adak:   {{-∞, 1983-10-30 12:00}, Bering}

America/Adak:   {{1983-10-30 12:00, ∞}, Hawaii_Aleutian}

America/Anchorage:      {{-∞, 1983-10-30 11:00}, Alaska_Hawaii}

America/Anchorage:      {{1983-10-30 11:00, ∞}, Alaska}

America/Juneau: {{-∞, 1983-10-30 09:00}, America_Pacific}
America/Juneau: {{1983-10-30 09:00, ∞}, Alaska}

America/Nome:   {{-∞, 1983-10-30 12:00}, Bering}

America/Nome:   {{1983-10-30 12:00, ∞}, Alaska}

America/Yakutat:        {{-∞, 1983-10-30 10:00}, Yukon}

America/Yakutat:        {{1983-10-30 10:00, ∞}, Alaska}

Pacific/Honolulu:       {{-∞, 1983-10-30 11:00}, Alaska_Hawaii}

Pacific/Honolulu:       {{1983-10-30 11:00, ∞}, Hawaii_Aleutian}

Pacific/Johnston:       {{-∞, 1983-10-30 11:00}, Alaska_Hawaii}

Pacific/Johnston:       {{1983-10-30 11:00, ∞}, Hawaii_Aleutian}

<metazone type="Alaska">

<long>

<generic>Alaska Time</generic>

<standard>Alaska Standard Time</standard>

<daylight>Alaska Daylight Time</daylight>

</long>

<commonlyUsed>true</commonlyUsed>

</metazone>

<metazone type="Alaska_Hawaii">

<long>

<generic>Alaska-Hawaii Time</generic>

<standard>Alaska-Hawaii Standard Time</standard>

<daylight>Alaska-Hawaii Daylight Time</daylight>

</long>

</metazone>

<metazone type="Hawaii_Aleutian">

<long>

<standard>Hawaii-Aleutian Standard Time</standard>

</long>

<commonlyUsed>true</commonlyUsed>

</metazone>
