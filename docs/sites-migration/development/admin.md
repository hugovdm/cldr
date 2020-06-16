# CLDR Trac Administration

## [TOC]

## Moot with Jira

## ~~CLDR Trac Administration~~

### ~~Adding a user~~

1.  ~~The password file is in apache's auth directory, named `cldr-trac.auth`~~
    1.  ~~Optional: use the command `apg -M NCL -n 1` to generate a random password.~~
    2.  ~~run the command~~
        ~~`/usr/bin/htdigest /etc/httpd/auth/cldr-trac.auth cldr-trac ***<user>***`~~
        ~~to append the user to the `cldr-trac.auth` file.~~
    3.  ~~If an error occurs, cldr-trac.auth may be manually edited to remove old entries before re-adding with the htdigest command.~~
2.  ~~Assign permissions in trac,~~
    ~~EITHER:~~
    ~~`# trac-admin /home/trac/cldr-trac permission add <`***`user>`***` developer`~~
    ~~OR~~
    ~~**Add** if you are an admin user in trac, go to http://unicode.org/cldr/trac/admin/general/perm and "**Add Subject to Group**" with Subject: ***`<user>`*** and Group: `developer` - then click~~
3.  ~~Edit `/home/trac/cldr-trac/conf/trac.ini` and add the user to the line
    containing `revw.options`~~
4.  ~~Log in once as the user (or have the user log in) to create their user record. Be sure to set the Full Name and Email address in Preferences.~~
5.  ~~Restart the web server by running "apachectl graceful" as root.~~
