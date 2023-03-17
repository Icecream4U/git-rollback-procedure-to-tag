# git rollback on tag procedure

## procedure to rollback main/master to a previous tag
:warning: due to limitations on the `protected` branches if a user is not abled to perform force push, the user will not be able to perform a rollback. You need to be allowed to force push on main/master to rollback to a previous tag!!!

`git checkout main` checkout main/master branch           
`git reset --hard v5.0` reset the HEAD of the branch to tag v5.0          
`git push -f origin main` force push the change of HEAD to main/master

now the main/master branch is aligned to tag v5.0        


if you want to return to a specific tag to work to modifications to solve the issues that caused the rollback, you can simply do:          
`git checkout -b return-to-v6-to-fix-it v6.0` to create a branch that has sources in the v6.0 tag versiong



## basic git commands:

`git tag` to list all the tags          
`git tag -l "search-test-with-wildcards-*` to list all the tags that matches the parameter           

`git tag -a v1.0 -m "first version with tag"` to create an annotated tag        
`git show v1.0` show all git tag data

`git tag v2.0-lw` to create a lightweight tag (no info about tagger, nor message. it's like a branch)     

`git log --pretty=oneline` show the commit history          
`git tag -a v2.0 -m "produce annotated 2.0 version from an old commit" 4dc5f612` create a tag for a specific commit in the past

`git push origin v2.0` the standard git push don't push tag, we have to explicity push them                    
`git push origin --tags` pushes all the tags in the local branch to remote server

`git tag -d v2.0-lw` delete a tag           
`git push origin --delete v2.0-lw` to remove the deleted tag also on remote server

## working with tags and branches:

`git checkout v3.0` move your sources to the tag version but put your repository in "detached HEAD" state. If you commit in this state your commit won't belong to any branch. `git switch -c <new-branch-name>` to create a new branch or `git switch -` to discard modifications and return to your branch as it was before (undo changes)                         

`git checkout -b <new-branch-name> v3.0` create a new branch aligned with the tag          


