# How to change the Survey Tool

# After any change, notify Rick to rebuild, test, and post.

## Tests

1.  To add a new test, look at /test/CheckCLDR.
2.  To add or modify new help text, change:
    1.  <http://unicode.org/cldr/data/tools/java/org/unicode/cldr/util/data/test_help_messages.html>
    2.  http://unicode.org/cldr/data/tools/java/org/unicode/cldr/util/data/chart_messages.html
    3.  Wiki text -
        http://www.unicode.org/cldr/wiki?SurveyToolHelp/CheckCoverage, and so
        on.
3.  You can add more files with editable HTML messages in them, and read them in
    code with the function ExampleGenerator.getHelpHtml()
4.  Note: Steven/Mark to add **keyed** message after: \[?\]
    *   *For details and help on any item, zoom in by clicking on the status
        icon: , , , , link for Help to*
        http://unicode.org/cldr/data/docs/survey/windows.html (*Mark*)
    *   See below

See also:

*   <http://unicode.org/cldr/data/tools/java/org/unicode/cldr/test/package.html>
*   <http://unicode.org/cldr/data/tools/java/org/unicode/cldr/tool/package.html>

## Coverage

To modify converage goals, change the Locales.txt file. Only change your
organization's goals.

1.  <http://unicode.org/cldr/data/charts/supplemental/coverage_goals.html>
2.  <http://unicode.org/cldr/data/tools/java/org/unicode/cldr/util/data/Locales.txt>
3.  Unless we run into perf problem, keep separate coverage.
4.  Replace country-specific locales by language locales unless spelling is
    different.

## General Instructions

Updating General instructions for users.

1.  http://www.unicode.org/cldr/data/docs/web/survey_tool.html
2.  http://www.unicode.org/cldr/data/docs/survey/windows.html
3.  http://www.unicode.org/cldr/data/docs/web/process.html#resolution_procedure
4.  http://www.unicode.org/cldr/wiki?SurveyToolDev/KnownBugs

## New Items

For a warning message on new items, change the regex in CheckNew

## Templates

*   Templates are found in the directory
    <http://unicode.org/cldr/data/tools/java/org/unicode/cldr/web/data/root/tmpl/>
    such as **dataitems_header.jsp**
    *   icons and other jsps are in the parent directory
*   At a basic level, templates can contain raw HTML. But they are full
    [JSP](http://java.sun.com/products/jsp/) pages.
*   Once checked in, Rick must rebuild and redeploy to test.

**Enabling Templatization**

*   call **ctx.includeFragment("dataitems_header.jsp")**
*   can use **ctx.put("key", value)** and (from the JSP****) ctx.get("key")****
    to pass data to the JSP

---

Adding Unit Tests to the Survey Tool (advanced)
if you add a file such as
"...cldr/tools/java/org/unicode/cldr/web/data/root/tmpl/r_unittest.jsp" (
example contents below ) you can run it as: (for example)
http://127.0.0.1:8080/cldr-apps/survey?_=de_CH&x=r_**unittest**

Hello! Here are a bunch o' xpaths for null (de_CH):
//ldml/identity/language\[@type="de"\]
//ldml/localeDisplayNames/territories/territory\[@type="ST"\]
//ldml/numbers/symbols/group
//ldml/localeDisplayNames/territories/territory\[@type="MH"\]
//ldml/delimiters/quotationEnd

NOTE: currently you have to make "getUserFile" public, like 4780 of
SurveyMain.java
r_unittest.jsp:
<%@ include file="stcontext.jspf" %>
<%@ page import="org.unicode.cldr.util.\*" %>
<%@ page import="org.unicode.cldr.test.\*" %>
<%@ include file="report.jspf" %>
<% synchronized(ctx.session) { /\* protect the DB access \*/ %>
<%
// note: next function is private, need to make it public.
SurveyMain.UserLocaleStuff uf = ctx.sm.getUserFile(ctx,
(ctx.session==null)?null:ctx.session.user, ctx.locale);
CLDRFile unresolvedFile = uf.cldrfile;
CLDRFile resolvedFile = new CLDRFile(uf.dbSource,true);
CLDRFile baselineFile = ctx.sm.getBaselineFile();
CheckCLDR check = uf.getCheck(ctx);
%>
Hello! Here are a bunch o' xpaths for <%= ctx.localeString() %>:
<ol>
<% for(java.util.Iterator iter = unresolvedFile.iterator();iter.hasNext();) { %>
<li>
<%= (String)iter.next() %>
</li>
<% } %>
</ol>
<% }/\* end sync \*/ %>
