# Updating JSON data

CLDR's JSON data is now maintained in a git repository, outside of CLDR's SVN.
To regenerate the JSON, do the following (you must have GitHub access to the
**unicode-cldr** organization). You also need - “github-release” and a github
key - go get it from <https://github.com/aktau/github-release>

1.  cd <CLDR_DIR>
2.  *# get the latest, or whatever tag*
3.  svn up
4.  mkdir git
5.  cd git
7.  *# I started with ‘RP=“cldr-core cldr-units-modern … “ - YMMV. I'm not sure
    how best to initially populate this.*
8.  RP="cldr-cal-buddhist-full cldr-cal-buddhist-modern cldr-cal-chinese-full
    cldr-cal-chinese-modern cldr-cal-coptic-full cldr-cal-coptic-modern
    cldr-cal-dangi-full cldr-cal-dangi-modern cldr-cal-ethiopic-full
    cldr-cal-ethiopic-modern cldr-cal-hebrew-full cldr-cal-hebrew-modern
    cldr-cal-indian-full cldr-cal-indian-modern cldr-cal-islamic-full
    cldr-cal-islamic-modern cldr-cal-japanese-full cldr-cal-japanese-modern
    cldr-cal-persian-full cldr-cal-persian-modern cldr-cal-roc-full
    cldr-cal-roc-modern cldr-core cldr-dates-full cldr-dates-modern cldr-json
    cldr-localenames-full cldr-localenames-modern cldr-misc-full
    cldr-misc-modern cldr-numbers-full cldr-numbers-modern cldr-rbnf
    cldr-segments-modern cldr-units-full cldr-units-modern"
9.  *# clone all repos. just get one depth, we don’t need all data locally.*
10. for repo in ${RP}; do git clone --depth=1
    git@github.com:unicode-cldr/${repo}.git; done
11. *# make a branch ‘for-30’ for everything.*
12. for repo in ${RP}; do (cd $repo ; git checkout -b for-30 ) ; done
13. *# now, let’s update some data*
14. cd cldr-json
16. *# At this point, please update **README.md** as appropriate*
18. *# this will clear out data in ../cldr-\*/*
19. ant clean
21. *# Rebuild data - takes ~40min on an 8-core 2.5 GHz Intel Core i7*
22. ant
23. cd ..
25. *# Check the data*
26. (TBD: How to test?)
28. # commit the data, push branch ( for beta )
29. for repo in ${RP}; do (echo $repo ; cd $repo ; git commit -m 'Generate CLDR
    30 data from r13032' --all ; git push ) ; done
31. # merge from branch and push signed tag to master
32. for repo in $(ls); do ( cd $repo && git checkout master && git merge for-30
    && git branch -d for-30 && git tag -s -m 'CLDR 30 from r13034' 30.0.0 && git
    push --tags && git push ); done
34. *# release the repos! This will create a 'github release' with .zip and .tgz
    files for each tag.*
35. for repo in $(ls); do ( github-release 2>/dev/null >/dev/null info -u
    unicode-cldr -r ${repo} -t 30.0.0 || ( echo missing $repo ; github-release
    release --user unicode-cldr --repo ${repo} --tag 30.0.0 --name 30.0.0
    --description "CLDR 30 @r13034 - see
    http://cldr.unicode.org/index/downloads/cldr-30" ) ); done
