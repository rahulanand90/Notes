# Git

Raw Topics

1. upstream vs downstream

### Git Basics - Initializing Git
##### git init
This locally initializes a database in the folder `.git`. Your repository is entirely stored within this .git folder 
##### HEAD 
The HEAD file is key in `.git` folder - it points to the current branch or commit ID you are currently on within 
your Git repository. 

##### config
The config file stores information about your repository’s local configuration. For example, the branches and remote 
repositories your repository is aware of. 

### Git Basics - Looking at Repo's History
git log

git status

Untracked file(s)


You can commit changes to files and add at the same time by doing git commit -a:
`git commit -a -m "Another message"`


#### git clone and reset
The git clone command helps you create copies of Git repositories to work on.

The git reset command helps you return to a previous or known state.

In these situations, many users delete the entire repository and re-clone. But often, all that’s needed is a hard 
reset. 


`grep -A2 'remote "origin"' .git/config`
You will see a new section that indicates where this Git repository was cloned from, and it gives that remote a name 
by default: origin. 


```shell
git log
git log --oneline
git log --oneline --graph
git log --decorate --graph --oneline
git log --decorate --graph --oneline --all
```

`git reset`
By default, Git will recover whatever has been added to the index/staging area and place it in your working 
directory. By contrast, a `git reset --hard` will blitz all local and added changes, reverting your checkout to a 
just-cloned and committed state.  

##### Detached Heads

##### tags

