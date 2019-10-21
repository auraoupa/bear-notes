# GIT
#git

git remote show origin

erreur : No refs in common and none specified; doing nothing
solution : git push -f -u origin master




 when : remote: error: GH001: Large files detected.

do : git filter-branch -f —index-filter ‘git rm —cached —ignore unmatch [NATL60-CJM165_Tu_20120901_AC.nc](http://natl60-cjm165_tu_20120901_ac.nc/) ‘

cf : [Fixing the “GH001: Large files detected. You may want to try Git Large File Storage.”](https://medium.com/@marcosantonocito/fixing-the-gh001-large-files-detected-you-may-want-to-try-git-large-file-storage-43336b983272)
