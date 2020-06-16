# CLDR Resolver tool

#### General Notes

##### Memory and CPU Usage

This tool requires a fairly high-end computer to run quickly. On modern
hardware, you should expect it to take *at least* half an hour per run, and at
least 1.5 hours to run the test suite (not part of a normal run). Due to fairly
aggressive caching in use in the CLDR Java libraries, this tool uses a lot of
memory. In order for the tool to work, you will need to increase the maximum
heap space allocated to the JVM to avoid OutOfMemoryErrors. We recommend 2500M
for normal runs and 3500M for test runs (though you can likely get away with
less, these values will definitely work). This can be set with the JVM
command-line parameter -Xmx<size> (e.g., -Xmx2500M).

#### Command-Line Usage

##### Locale

\[-l|--locale <localeregex>\]

This option allows you to specify a regular expression matching the locales that
you want to output

**Default**: .\*

**Example**: -l en.\*|de_DE

##### Destination Directory

\[-d|--destdir <destination-directory>\]

This option allows you to specify a directory where the resolved .xml files will
be output.

**Default**: Current working directory

**Example**: -d /home/username/cldr-resolved

##### Source Directory

\[-s|--sourcedir <source-directory>\]

This option specifies where the standard CLDR XML files are located. This should
be set to the common/main directory of the standard CLDR distribution. If not
specified, it will default to the CLDR_DIR environment variable (which can be
specified to the JRE with -DCLDR_DIR=value).

*Note: If this environment variable is not set, this parameter is required.*

**Default**: Value of CLDR_DIR environment variable

**Example**: -s /home/username/cldr/common/main

##### Resolution Type

\[-r|--resolutiontype <simple|full|nocode>\]

This option allows you to specify the type of resolution that will be performed.
The following options (and given aliases) are accepted:

*   **Simple Inheritance**
    *   *Description*:
    *   *Aliases*: s, simple, simpleinheritance, simple-inheritance, p, partial
*   **Fully-Resolved**
    *   *Description*: One file per locale. Everything including the kitchen
        sink. This eliminates all aliases and inheritance from the CLDR
        structure, and
    *   *Aliases*: f, full, fully, fullyresolved, fully-resolved
*   **Fully-Resolved without code-fallback**
    *   *Description*:
    *   *Aliases*: n, nc, nocode, no-code, nocodefallback, no-code-fallback

##### Draft Status

\[-m|--mindraftstatus <unconfirmed|provisional|contributed|approved>\]

This option allows you to specify the minimum draft status from which to return
results. Draft statuses may be identified by any shortening of the name by
truncation (e.g., u, prov, contrib, ap...)

*Note: The default is not specified in the tool, but is an artifact of the
implementation of CLDRFile.Factory. If the default draft status in CLDRFile is
changed, this will change accordingly. However, it is currently set to
unconfirmed.*

**Default**: unconfirmed

**Example**: -m approved

##### Verbosity

\[-v|--verbosity <0|1|2|3|4|5>\]

This option allows you to specify the verbosity level of the tool's output. 0
will output nothing, 1 will output errors only, 2 is fairly minimal output, 3 -
4 increase output slightly, and 5 will flood your terminal with every single
path/value pair processed by the tool.

**Default**: 2

**Example**: -v 0

#### Using the Output

##### NO_VALUE

Only relevant for Simple Inheritance: Due to the fact that the tool rewrites
parenting relationships, a situation may occur where a value (or rather an
XPath) does not occur in a child locale or any of its parents in the original
CLDR data, but does occur in the truncation parent. (This can happen when the
truncation parent is not the normal parent, e.g., zh_Hant's truncation parent is
zh but its CLDR parent is root.)

To handle this situation while still maintaining the inheritance structure, the
tool inserts a bogus "no value" entry at that XPath. This value will be
"\\uFFFDNO_VALUE\\uFFFD", where "\\uFFFD" represents the Unicode character
U+FFFD. This value will always be exactly this string, and when using the data,
you should ensure that this value is never used as valid data.
