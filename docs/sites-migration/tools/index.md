# CLDR Tools

## About this page

This page is designed for general consumers of CLDR. Members of the CLDR-TC
doing development on CLDR itself, or other curious parties, should see [New CLDR
Developers](../development/new-cldr-developers/index.md) and the [CLDR
Development](../development/index.md) pages instead.

## Obtaining CLDR Tools

You can either obtain CLDR tools by 1. downloading "**tools.zip**" from the
[CLDR Releases/Downloads](../index/downloads/index.md) page, or 2. checking out
the CLDR source tree as per the [CLDR Repository
Access](../development/cldr-repository-access/index.md) page. You will also
probably want to download the CLDR data itself from either of these two
locations.

## Prerequisites

Most of the CLDR tooling is written in Java. The [Java
JDK](http://www.oracle.com/technetwork/java/javase/downloads/index.html) version
1.8 or newer is required, as is [Apache Ant](http://ant.apache.org/).

## Building

```none
ant -f tools/java/build.xml jar
```

This will build tools/java/**cldr.jar**

## Running the tools

### Obtain a list of available tools

*   To verify your build of the CLDR tools, run the following command. It will
    print out a list of installed tools.

```none
java -jar tools/java/cldr.jar
```

*   Adding the `-l `option will list otherwise-undocumented or hidden tools.

### Running a specific tool

*   A tool is run by entering its **alias name** or **full package name** after
    "cldr.jar", followed by any other arguments or options.
    The following two command lines are identical:

<pre><code>java -jar tools/java/cldr.jar <b>validate</b>   <i>path/to/somefile.xml</i>
</code></pre>

<pre><code>java -jar tools/java/cldr.jar <b>org.unicode.cldr.util.XMLValidator</b>   <i>path/to/somefile.xml</i>
</code></pre>

### Tool environment settings

*   Many of the tools need to know where the CLDR data is located. This is
    accomplished by setting the `CLDR_DIR` variable. For example, if you have
    your CLDR data in `/somewhere/cldr` you might call a tool this way:

<pre><code>java <b>-DCLDR_DIR=/somewhere/cldr</b> -jar tools/java/cldr.jar ...
</code></pre>

*   If you run out of memory (not that it could happen with CLDR tools and
    data), you might need to prepend `-Xmx` or other options. See your JDK
    documentation.

<pre><code>java <b>-Xmx700M</b> -DCLDR_DIR=/somewhere/cldr-jar tools/java/cldr.jar ...
</code></pre>

### Tool Help

*   Many tools support the "`-h`" or "`-?`" options to display full help.
    Try adding these options if you are unsure of how to use a tool.

## Specific Tools

CLDR has a lot of tools. See the list of subpages below for specific
documentation. If a tool is not documented here, you might try the [CLDR
Development Site](../development/index.md) page or else file a bug.
