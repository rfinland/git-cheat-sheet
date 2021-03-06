```bash
git config
git config --global user.name "[rfinland]"

git config --global user.email "[r.rinland88@gmail.com]"
git config --global core.editor atom
git config --global --edit
```
#Used to list all the files that have to be committed:
```bash
git status
git status --long

git init
git status
git add
git commit -m ""
```
#Remove staged file:
```bash
git rm --cached  dummy.txt
```
#Remove All Staged Files/Directories (staged means all stuff those who added )
```bash
git rm --cached -r .
```

#Git diff between what you added and what is
```bash
git diff
```
#list of commits
```bash
git log
git log --oneline
git log -3 --oneline
git log -p
git log --stat
```
#Undo Changes:
#Before Add
```bash
git restore -- dummy
#After Add
git restore --staged dummy
```
#Undo commit:
First check out list of the commits:
```bash
git log --oneline
```
In my case:
```bash
5314de1 (HEAD -> master) M files
9d0eefb M files
caddc3f M files
29e89e3 init
```
I'm going to switch to caddc3f
```bash
git reset caddc3f
git reset --hard caddc3f
git checkout <commit hash>
git revert <commit hash>
```
- If you want to test the previous commit just do git checkout <test commit hash>; then you can test that last working version of your project.
- If you want to revert the last commit just do git revert <unwanted commit hash>; then you can push this new commit, which undid your previous commit.
- To fix the detached head do git checkout <current branch>.

# git branch:
```bash
git branch dev
git branch -a
git checkout dev
git checkout master
git branch -d dev
```
#Other way to create:
```bash
git checkout -b develop
```

#Merge:
```bash
git checkout master
git merge develop
git log --graph
```
#Git stash
#Save temp commits on a branch Without see Modified files on the other branch
#on your develop branch (in my case)
```bash
git stash
git stash save "Pre commit"
git stash list
git stash  show -p stash@{0}
git stash apply stash@{0}
git stash pop stash@{0}
git stash drop  stash@{1}
```


#.ignore file sample:
```bash
node_modules/
*.txt
!a.txt
```
#If you have had a commited file and now you wanna add it to ignore file:
```bash
git rm --cached -r .
git add .
git commit -m "M"
```


#Remote
```bash
git remote add origin https://github.com/rfinland/git-cheat-sheet.git
git remote
git branch -M master
git push -u origin master
git push -u origin develop
```

#bisect
```bash
git bisect start
git bisect good <Choose Hash when it was good>
#test it and add re-action (bad-good)
git bisect bad
#OR
git bisect good
```
```bash
When you found out which commit ruined everything then:
git bisect reset
```