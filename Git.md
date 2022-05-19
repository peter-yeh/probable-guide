# Git

| Terms | Meaning |
| --- | --- |
| Origin | Origin === probable-guide.github.com. Origin is a variable which points to the URL which stores the remote repo |
| Remote | A repo in the cloud. `origin` points to the remote repo |

## Basic git commands
#### Download repo
`git clone https://github.com/peter-yeh/reponame.git`

#### Get change from github
`git pull`

#### Check status of current branch
`git status`

#### See the commit log
`git log`

#### See the commit tree
`git log --graph`

#### Stage all changes
`git add .`

#### Commit the changes
`git commit -m 'First commit'` 

#### Push the commits to github
`git push`


## Staging/committing
##### Discard all non committed files
`git clean -df`

#### Remove non staged files
`git restore .`


## Stash
#### Create a stash with the name
`git stash save "stash message"`

#### Stash uncommitted files
`git stash -u`

#### Check the stashes
`git stash show`

#### List the stash
`git stash list`

#### Reapply the stash
`git stash pop`


## Git merging files
#### Merge feature branch into current branch
`git merge feature` // call in master branch

##### Abort merge conflict
`git merge --abort`


## Git editing history
#### un-commit but don't un-stage
`git reset --soft HEAD^`

#### un-commit and un-stage
`git reset HEAD^`

#### Update the git repo in origin after changing the commit tree
`git push origin +HEAD`

#### Force push local history after changing commit tree
`git push -f origin branchName`

## Git config settings
``` properties
# Store the password
git config credential.helper store

# Set the username, --global for global
git config --global user.name
git config --global user.email
```
