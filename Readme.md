# the basics
### get a project up and running
`git status;` # this should show no repository initialized.
<br>`git init;git checkout -b dev;git add .; git commit -m "your message"; git push;`

### workflow for making changes to a repository.
`git add .; git commit -m "your message"; git push;`

### Branches
#### checkout to a branch:
notice this command will not work until the branch is created.
<br>`git checkout branch_name;`
#### create a new branch:
`git checkout -b branch_name;`

### some notes for the basics.
`git status;` - will help you reason about what needs to be done next.
<br>`git log;` - will help you reason when you become more advances and start messing with git SHA's
<br>`git log --patch;` - will show the log along with all the changes each commit contributed.hit spacebar to quickly move through this output.

#### notes on branches:
by default when a repository is initialized it is on master
<br>People who want the stable version of your project 
<br>will download the master version of your project.
<br>In "get a project up and running we created a new branch called dev.
<br>having a dev branch is important because it is a place where you can push
<br>code that works but needs review and acceptance before dubbed stable for users.

When a developer builds a new feature they should do so on a newly created branch(also known as topic banch).
<br>then they open a merge/pull request into the dev branch.
<br>later dev branch will open a merge/pull request to master branch.

After a new branch(topic branch) completed its feature and is merged it should be deleted.
<br>dev branch and Master branch should not be deleted. 
<br>dev branch is for not building additional features therefore does not need cleaning up..
<br>think of dev branch as a code placeholder that new branches merge onto.

### merge vs rebase, what is the difference (they both update branches.)?
merge takes your changes and puts them on top of the current branch.
<br>you should merge onto master but never rebase. We do not want to change the base of the master branch.
rebase moves the branch like master to the base of your branch.
<br>then it individually puts your changes on top.
<br>rebase is a better practice for updating one of the feature branches to be identical to master with your changes on top but a harder operation because if the branch differs instead of one merge conflict to resolve you could potentially have a merge conflict for every commit that differs from the branch.
<br>therefore I prefer to git rebase and if there is a merge conflict git rebase --abort.
<br>and switch to a git merge.

git merge puts the changes of the branch being merged on top of the current branch.
And resolves everything in a single large merge conflict if there is one.
```
git checkout dev; git rebase -;
git checkout dev; git merge -;
```


