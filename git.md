# Git

https://learngitbranching.js.org/

## Intro in Sequence

### Git Commit

|  Command   | Description    |
| :--------: | :------------- |
| git commit | Commit changes |

### Branching

|             Command             | Description                                 |
| :-----------------------------: | :------------------------------------------ |
|           git branch            | List branches (local)                       |
|          git branch -a          | List branches (local & remote)              |
| git checkout -b `<branch_name>` | Create new branch and switch to that branch |

### Merging

|          Command          | Description                          |
| :-----------------------: | :----------------------------------- |
| git merge `<branch_name>` | Merge other branch to current branch |

### Rebasing

|             Command             | Description                                           |
| :-----------------------------: | :---------------------------------------------------- |
| git rebase `<base_branch_name>` | Merge other branch to current branch (cleaner commit) |

## Ramping Up

### Detach Head

|               Command               | Description                                                |
| :---------------------------------: | :--------------------------------------------------------- |
|    git checkout `<commit_hash>`     | Detach HEAD from branch and into commit                    |
| git checkout -b `<new_branch_name>` | Create a new branch for commit done in Detached HEAD state |

- **Review history**: View past commit codes and can test
- **Detached HEAD state**: NOT ON A BRANCH, so changes won't affect existing branches unless explicitly commited to a new one.
- Can Edit, Stage, Commit, but will garbage collected if not saved in a new branch

### Relative Refs (^)

|               Command                | Description                                                                   |
| :----------------------------------: | :---------------------------------------------------------------------------- |
| git checkout `<branch/commit_hash>^` | Move to the relative ref (^) parent of a branch current commit or commit hash |

### Relative Refs (~)

|                    Command                    | Description                                                                                                                         |
| :-------------------------------------------: | :---------------------------------------------------------------------------------------------------------------------------------- |
| git branch -f `<branch_name>` `<target_name>` | **Branch Forcing**: reassign a branch to a commit                                                                                   |
|         `<branch/commit_hash/HEAD>~N`         | Use **Branch Forcing** or checkout to move to the relative ref (~) parent by **N** number of a branch current commit or commit hash |

### Reversing Changes

|             Command              | Description                                                                                                                |
| :------------------------------: | :------------------------------------------------------------------------------------------------------------------------- |
| git reset `<commit_hash/HEAD>~N` | (local) undo a commit on current local branch, deleting the future commit                                                  |
| git revert `<commit_hash/HEAD>`  | (remote) create new commit without changes from mentioned commit to fix a remote commit, then can git push again to remote |

- **git reset**: rewriting history, move a branch backwards as if the commit had never been made in the first place.
- **git revert**: create new future without changes of latest commit.

## Moving Work Around
