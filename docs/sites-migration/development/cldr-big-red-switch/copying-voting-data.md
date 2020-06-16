# S3. Copying Voting Data

1. Make sure you have a workspace for the voting results\*.

```none
svn co  svn+ssh://unicode.org/repos/cldr-aux/voting ~/src/cldr-aux-voting-archive --depth=immediates
```

2. copy the voting data locally such as with

```none
rsync --exclude=.svn --delete-excluded --exclude=users  -av st.unicode.org:/home/surveytool/tomcat/cldr/vetdata/ ~/src/cldr-aux-voting-archive/33/
```

(You can copy another way, just make sure that the "users" directory is not
copied as it contains users' email addresses.)

3. Double check that users.xml is NOT included (users**a**.xml is OK, A is for
anonymous and doesn't include addresses)

4. add and commit the data.

```none
svn add 33
svn commit -m 'checkin CLDR 33 data' 33
```

5. double check the data at <https://unicode.org/repos/cldr-aux/voting/33/> that
it looks correct

———

\* ` --depth=immediates `keeps you from having to fetch everything. You can
later use `svn up --set-depth=infinity `to fetch the rest of the content, see[
"Sparse Directories"
(SVNBook)](http://svnbook.red-bean.com/en/1.7/svn.advanced.sparsedirs.html)
