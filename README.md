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
``` 
git diff --staged HEAD
git difftool --staged HEAD
```
cmd q to quit
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
#####branch

```
git branch -a
```
change name
```
git branch -m oldname newname
```
compare branch
```
git diff br1 br2
```
ff merge: git put all commits from other branch to master branch. (does not create new commit)  
--no-ff : will create a new commit, old branch's commit will not put on new commit.  

Automatic merge:
```
git branch other -m "message"
```
#####rebase
if we are on new branch(the branch is in development),also we want to get newest feature from master branch, we can rabase current branch on master branch
```
(newbranch)git rebase master
```
If both branchs have commits and confilct happens, to abort,
```
git rebase --abort
```
to resolve,
```
git rebase master
git mergetool
git add confile
git rebase --continue
```
######rebase from remote branch
```
git fetch origin master  //do not use pull.
(master)git pull --rebase origin master
```
#####stash
######basic
```
git stash(in working dict, not in stage dict) = git stash save
```
restore to working dict:
```
git stash apply
```
cleanup
```
git stash list 
git stash drop
```

#####stash untracked files(by default stash only tracked files)
```
git ls-files //list all tracked files
```

stash all files(including untracked files)
```
git stash -u
```
more convenient
```
git stash pop=apply+drop
```
######multi stash
```
git stash save "message"
```
```
git stash show stash@{1}  //shiw diff
```
```
git stash apply stash@{1}
```
```
git stash clear //drop all
```
######stash in another branch
```
git stash branch newbranch  //stash dropped, all changes(untracked, tracked but ont staged) will be restored
```
#####tag
######1 lightweight
```
git tag tagname
git tag --list
git show tagname(show latest commit)
git tag --delete tagname
```
######2 annotated
```
git tag -a 1.0 //then type in editor
git tag show 1.0
```
######3 compare
another syntax to type message:
```
git tag 1.0 -m "message"
git diff(tool) tagname tagname
```
###### tag on a apecific commit
```
git tag -a 1.0 444111
```
###### change a existing tag to another commit
```
git tag -a 1.0 -f 555111
```
###### push
```
git push origin tagname (also push the corresponding commits, if not pushed)
```
```
git push origin master --tags
```
deelte a tag on remote
```
git push origin :tagname    // (nothing for remote) : tagname
```
