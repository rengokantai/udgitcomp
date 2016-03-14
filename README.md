#### udgitcomp


#####6
######1 visual merge.
perforce p4merge for windows  
only install visual merge tool

######3 config
```
git config --global diff.tool p4merge
git config --global merge.tool p4merge
git config --global difftool.p4merge.path "C:/Program Files/Perforce/p4merge.exe"
git config --global mergetool.p4merge.path "C:/Program Files/Perforce/p4merge.exe"
git config --global difftool.prompt false
git config --global mergetool.prompt false
```
check
```
git config --global --list
```
######5 mac config
```
~/.gitconfig
```

like this:
```
[user]
  name = ke
  email = @
[core]
  editor = mate -w
[alias]
  hist = log --all --graph --decorate --oneline
```

some change:
```
git config --global difftool.p4merge.path "/Application/p4merge.app/Contents/MacOS/p4merge"
```

#####7
######1 compare working dic and staging area
```
git diff 
```
```
git difftool
```
######2 compare working dic and repo(last commit)
```
git status
git diff HEAD
git difftool HEAD
```
######3 compare staging area and repo(last commit) 
``` cmd q to quit
git diff --staged HEAD
git difftool --staged HEAD
```
######4 compare to one file
```
git diff -- filename
git difftool -- filename
```
######5 compare commits
```
git log --oneline
git diff 123456 HEAD    //syntax: older newer
git diff HEAD HEAD^
```
######compare local and remote master branch
```
git diff master origin/master
```

