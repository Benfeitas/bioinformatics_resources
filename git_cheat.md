
# Git cheat sheet
## Most used commands:
1. `git init`                                           #makes the current directory as a git directory
2. `git remote add origin [URL]`         #adds the URL
3. `git pull origin master`                   #pulls everything from remote to local
4. `git status`                                      #checks for changes
5. `git add [FILE]`                               #adds each file
6. `git commit`                                    #commits added files
7. `git push origin master`                  #pushes all changes to remote


## Main commands
`git status -s`                    #short description for status
`git add [file]`                    #adds file
`git commit`                    #commits to current branch
`git log --oneline`                #shows git 1st (main) message
`git checkout [branch_name]`            #switches between branches
`git checkout -b [newbranch]`            #creates and changes to branch
`git branch`                    #shows all branches
`git merge [branch_name]`            #merges branch to master
`git branch -d [branch_name]`            #deletes branch
`git diff`                        #differences in the current branch not added
`git diff --staged`                #differences that were staged
`git checkout -- [file]`                #discards currently unstaged changes
`git remote add origin [url]`            #adds URL to a remote repo
`git remote -v`                    #shows URLs of repo
`git push origin master`                #pushes changes to master
`git pull origin master`                #pulls changes from a remote
`git clone [url]`                    #clones remote and creates a new dir
`git clone [url] .`                    #clones remote to current dir
`git tag [name]`                    #adds a tag with a name
`git tag -a [name]`                #adds annotation (commit message) to tag
`git push --tags origin master`            #pushes tags to remote
`git remote set-url origin [url]`            #changes the URL of the local repo            


## Staging steps
Tracked =========== Staged ============================== Committed
change ===[git add]======>to be committed====[git commit]=========>Commit
    
**Writing good commit message:** [https://chris.beams.io/posts/git-commit/](https://chris.beams.io/posts/git-commit/)

## Git config 
Add to the git config:
    To configure write for instance git config --global core.editor “vim”
user.name
user.email
[optional] core.editor

## Ignoring files
**.gitignore**
Information that should be ignored from git changes. Is a normal text file
*.xlsx
*.fastq
data/*

## Branches:
    Allow you to work in parallel in the same repo
`git branch`   # check which branch you are
`git checkout -b <new_branch>`   # to create new branch
`git checkout <branch>`   # to change to the new branch 
`git merge new_branch`   # To make the changes in new_branch to be in `master`
`git branch -d <new_branch>`    # delete the branch new_branch

##File differences:
    Finds only unstaged (uncommitted) changes in files.
`git diff [file]`     

##Managing conflicts:
Always pull before pushing
To solve issues, try to solve before committing/adding
Issues must be solved manually
If issues arise in different locations of a file, they are usually merged.    

##Forks:
Are copies of entire repositories
Use when you want to complement an existing repo with features, tools, etc. and don’t have permissions to branch
It is an alternative to git clone

