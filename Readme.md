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
<br>`git log --patch;` - will show the log along with all the changes each commit contributed.
<pre>       hit spacebar to quickly move through --patch  output.</pre>

### lets talk about remote:
local are the branches on your computer. 
remote means off your computer on the internet.

when you clone down a project the project automatically remembers the url and assigns it a nickname remote "origin"

if you initialize a project you must add the remote yourself:
<br>`git remote add cheese https://github.com/MichaelDimmitt/introduce_users_to_cool_git.git`

you can check what remotes you have for your project by the command:
<br>`git remote -v`

you can give a remote any nickname you want. In this case we made it cheese.
<br>we use remote to push the code. they default to origin or the only remote availiable.
<br>this is why `git push` works.
<br>however the actual command when you type git push and are on master branch is... 
`git push origin master;`

sometimes when you push you will see it prompting you --upstream. 
<br>this means that the remote does not currently have that branch and you are adding it.

#### notes on branches:
by default when a repository is initialized it is on master
<br>People who want the stable version of your project 
<br>will download the master version of your project.
<br>In "get a project up and running we created a new branch called dev.
<br>having a dev branch is important because it is a place where you can push
<br>code that works but needs review and acceptance before dubbed stable for users.

When a developer builds a new feature they should do so on a newly created branch.
<br>then they open a merge/pull request into the dev branch.
<br>later dev branch will open a merge/pull request to master branch.

After a new branch completed its feature and is merged it should be deleted.
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

# Intermediate git section:
`git log;`
### Squasing made simple:
I put the `git log` above because I used to use it to figure out how far back to rebase so that my squashing would work and not break anything by going too far back. 

However, it just became easier. you can squash simply by ... 
<br>`git checkout dev;git rebase -i master;`
<br>dev should always be ahead of master and master should always be the base.
<br>the command looks specifically at the changes dev has on top of master and gives you the oppertunity to squash and perform any other operations and nothing there will never adversely affect the master branch. welcome to the future. If you have any questions about this shoot me an email or message me on slack or twitter. 
<br> unless everyone already knew this stuff and im late to the party. 😘 . 
https://stackoverflow.com/questions/49968345/git-rebase-i-from-top-of-another-branch-squashing-made-simple/49968346#49968346

### Cherrypicking
http://stackoverflow.com/questions/9339429/what-does-cherry-picking-a-commit-with-git-mean
1) Make sure you are on the branch you want apply the commit to.
 ```git checkout master```
2) Use `git log;` to find the commit hash you are looking for.  
3) Execute the following:
 ```git cherry-pick <commit-hash>```
