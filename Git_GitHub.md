# Git/GitHub

## Git  
> Git is a free and open source distributed version control system designed to handle everything from small to very large projects with speed and efficiency.
>
> Git is easy to learn and has a tiny footprint with lightning fast performance. It outclasses SCM tools like Subversion, CVS, Perforce, and ClearCase with features like cheap local branching, convenient staging areas, and multiple workflows.  
[https://git-scm.com/](https://git-scm.com/)

## GitHub  
> GitHub is a for-profit company that offers a cloud-based Git repository hosting service. Essentially, it makes it a lot easier for individuals and teams to use Git for version control and collaboration.  
(https://kinsta.com/knowledgebase/what-is-github/)[https://kinsta.com/knowledgebase/what-is-github/]

# Git
1. [Advantages of utilizing Git](#gitadvantages)
2. [Ways to use Git](#gitusecases)
3. [Basic Operations](#gitoperation)
4. [Reference](#gitreference)
5. [learning](#gitlearning)

<a id="gitadvantages"></a>

### 1. Advantages of utilizing Git

1. **Free and open-source**: No need to purchase and can be used anywhere.  
2. **Fast and small**: No need to connect to the central server. All the operations can be performed on the local copy stored on the developer machine making it really fast.  
3. **Implicit backup**: Every checkout is a full backup of the repository, hence multiple copies are available.  
4. **Security**: Git uses SHA1 algorithm to secure the data stored within the repository.  
5. **Easy branching**: Git branches are easy and cheap to merge. Every small change to your code creates a new branch.  
[https://k21academy.com/devops-foundation/git-overview-workflow-advantages/](https://k21academy.com/devops-foundation/git-overview-workflow-advantages/)

<a id="gitusecases"></a>

### 2. Ways to use Git  

| No | Command | Options | Description |  
| ---- | ---- | ---- | ---- | 
| 1 | push |  | Update remote refs along with associated objects. |  
| 2 | commit |  | Record changes to the repository. |  
| 2 | commit | --amend | Changing your most recent commit is probably the most common rewriting of history that you'll do. | 
| 2 | commit | -m <msg>, --message=<msg> | Use the given <msg> as the commit message.  | 
| 2 | -a, --all | -m <msg>, --message=<msg> | Tell the command to automatically stage files that have been modified and deleted, but new files you have not told Git about are not affected. |
| 3 | pull |  | Fetch from and integrate with another repository or a local branch | 
| 4 | add |  | Add file contents to the index | 
| 5 | revert |  | revert some existing commits | 
| 6 | checkout |  | Switch branches or restore working tree files. | 
| 7 | init |  | Create an empty Git repository or reinitialize an existing one | 


<a id="gitoperation"></a>

### 3. Basic Operations  

1. [Git clone](#clone)
2. [Git branch](#branch)
3. [Git checkout](#checkout)
4. [Git status](#status)
5. [Git add](#add)
6. []

<a id="clone"></a>

#### 1. ```Git clone```

```
$ git clone <https://name-of-the-repository-link>
```

<a id="branch"></a>

#### 2. ```Git branch```

**Creating a new branch:**

```$ git branch <branch-name>```


This command will create a branch locally. To push the new branch into the remote repository, you need to use the following command:  

```$ git push -u <remote> <branch-name>```

**Viewing branches:**

```$ git branch or git branch --list```

**Deleting a branch:**

```$ git branch -d <branch-name>```

<a id="checkout"></a>

#### 3. Git checkout

This is also one of the most used Git commands. To work in a branch, first you need to switch to it. We use ```git checkout``` mostly for switching from one branch to another. We can also use it for checking out files and commits.

```$ git checkout <name-of-your-branch>```


There are some steps you need to follow for successfully switching between branches:  

- The changes in your current branch must be committed or stashed before you switch  
- The branch you want to check out should exist in your local  

There is also a shortcut command that allows you to create and switch to a branch at the same time:

```$ git checkout -b <name-of-your-branch>```

<a id="status"></a>

#### 4. Git status  

The Git status command gives us all the necessary information about the current branch. 

```$ git status```

We can gather information like:

- Whether the current branch is up to date
- Whether there is anything to commit, push or pull
- Whether there are files staged, unstaged or untracked
- Whether there are files created, modified or deleted

<a id="add"></a>

#### 5. Git add  

When we create, modify or delete a file, these changes will happen in our local and won't be included in the next commit (unless we change the configurations).

We need to use the git add command to include the changes of a file(s) into our next commit.  

To add a single file:  
```$ git add <file>```

To add everything at once:  

```$ git add -A```


References  
- [10 Git Commands Every Developer Should Know](https://www.freecodecamp.org/news/10-important-git-commands-that-every-developer-should-know/)