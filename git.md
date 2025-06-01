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

|               Command               | Description                                                |
| :---------------------------------: | :--------------------------------------------------------- |
|    git checkout `<commit_hash>`     | Detach HEAD from branch and into commit                    |
| git checkout -b `<new_branch_name>` | Create a new branch for commit done in Detached HEAD state |

- **Review history**: View past commit codes and can test
- **Detached HEAD state**: NOT ON A BRANCH, so changes won't affect existing branches unless explicitly commited to a new one.
- Can Edit, Stage, Commit, but will garbage collected if not saved in a new branch
