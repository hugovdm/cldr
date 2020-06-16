# Easy Steps

**See also: [SurveyTool Info](../surveytool-info/index.md)**

**[TOC]**

## Quick Introduction

1.  They consist of [JSP](http://java.sun.com/products/jsp/) files. The API they
    use is still being documented, but you can create javadocs using the
    **docs** ant target of both the 'java' and 'cldr-apps' projects.
2.  The JSP files are located in the
    [WebContent/WEB-INF/tmpl](http://unicode.org/cldr/trac/browser/trunk/tools/cldr-apps/WebContent/WEB-INF/tmpl)
    directory in the cldr-apps project.
3.  The 'main()' jsp is **r_steps.jsp**
4.  The 'list of steps' is in **report.jsp**
5.  Look for jsps with names based on the 'list of steps', in the 'tmpl'
    directory for examples.

The easy steps load existing data, but only show it if there is current approved
data. It won't show if there's no data due to conflict. The easy steps page
doesn't just give people a blank field to fill in, the field will be preloaded
with any currently-approved (that is, winning) value.
Example:

*   <http://unicode.org/cldr/apps/survey?_=ar_AE&x=r_steps>
*   the 'your language' field isn't blank, it has the currently approved ar_AE
    data. If X different people enter the same data, we'll get X different votes
    for the same value.

'Easy steps:
[Step-By-Step](http://kwanyin.unicode.org:8080/cldr-apps/survey?_=aa&x=r_steps)'
comes from tmpl/report_menu.jsp . It provides a link to a JSP called "r_steps".

## JspWebContext

The 'ctx' / 'subCtx' objects used inside jsps now should be of the class
**JspWebContext**. Some new examples of use:

```none
subCtx.openTable(); 
subCtx.showXpath(new String[] 
                 {"//ldml/localeDisplayNames/territories/territory[@type=\"AC\"]",
                  "//ldml/localeDisplayNames/territories/territory[@type=\"TA\"]"});
subCtx.closeTable();
subCtx.openTable();  // a second table
subCtx.showXpath("//ldml/localeDisplayNames/languages/language[@type=\"yue\"]");
subCtx.showXpath("//ldml/localeDisplayNames/languages/language[@type=\"swb\"]");
            
subCtx.showXpath("//ldml/localeDisplayNames/variants/variant[@type=\"PINYIN\"]");
subCtx.showXpath("//ldml/localeDisplayNames/variants/variant[@type=\"WADEGILE\"]");
subCtx.closeTable();
```

After the last showXpath call,

```none
subCtx.doneWithXpaths();
```

must be called.

## Q&A

### **Q. How do I get this file included in the "chain" of Easy Steps**

'Easy steps:
[Step-By-Step](http://kwanyin.unicode.org:8080/cldr-apps/survey?_=aa&x=r_steps)'
comes from tmpl/report_menu.jsp . It provides a link to a JSP called
"r_steps".The chain is in the file "tmpl/**report.jspf**" ( these 'steps' were
originally called 'reports'. )

Add your steps' name to the **reports\[\]** array, and then, list the base xpath
in the **base_xpaths\[\]** array.

### **Q. What does setQuery mean?**

subCtx.setQuery(SurveyMain.QUERY_SECTION,subCtx.field(SurveyMain.QUERY_SECTION));

This sets the default working URL to contain the "x=" field. QUERY_SECTION, that
is "x", normally contains the section of the surveytool being visited: numbers,
characters, timezones, etc. It's sort of like setting the base URL.

### **Q. How is** printSectionTableOpenShort used?

> SurveyForum.printSectionTableOpenShort(subCtx,
> "//ldml/numbers/symbols/decimal");

> *SurveyForum.printSectionTableOpenShort(subCtx, **thisBaseXpath**);*

thisBaseXpath is the xpath that your current "step" is connected to.

TableOpen prints the opening HTML for the entire table (i.e. the header)

### **Q. What do these do?**

*SurveyForum.showXpathShort(subCtx, "//ldml/dates/calendars/calendar\[@type=\\"gregorian\\"\]/eras/eraAbbr/era\[@type=\\"0\\"\]");*
*SurveyForum.showXpathShort(subCtx, "//ldml/dates/calendars/calendar\[@type=\\"gregorian\\"\]/eras/eraAbbr/era\[@type=\\"1\\"\]");*

These each show a specific XPath's worth of data.

### Q. **What do these do?**

*SurveyForum.printSectionTableCloseShort(subCtx, thisBaseXpath);* SurveyForum.printSectionTableCloseShort(subCtx, "//ldml/numbers/symbols/decimal");

TableClose.. prints the closing HTML.

### Q. How do I add a new step?

1.  Edit report.jspf in the tmpl directory
    1.  Add the step's name to the reports\[\] array., for example "shoesize"
    2.  Add the base xpath the report will work with to the base_xpaths\[\]
        array (in the same position)., for example "//ldml/shoesize"
2.  Create shoesize.jsp (you might copy a simple example such as eras.jsp )
3.  Edit shoesize.jsp to include showing the specific xpaths you wish to show

### Q. How do I get the CLDRFile and SupplementalDataInfo?

CLDRFile file = SurveyForum.getCLDRFile(subCtx);
SupplementalDataInfo supplementalData =
SupplementalDataInfo.getInstance(file.getSupplementalDirectory());

### Q. How do I get a link to a ST section?

<a href="<%= ctx.base(request)+"?_="+ctx.getLocale()+"&x=languages"
%>">languages</a>
