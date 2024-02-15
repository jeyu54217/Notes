

- [**REMOTE**](#remote)
  - [clone](#clone)
  - [push](#push)
  - [pull](#pull)
- [**STAGING**](#staging)
  - [add](#add)
- [**LOCAL**](#local)
  - [Branching and Merging](#branching-and-merging)
- [Stash](#stash)
- [Checking Status and Logs](#checking-status-and-logs)

## **REMOTE**
### clone
  ```bash
  git clone 
  ```
### push
  ```bash
  git push
  ```
  ```bash
  git push origin <branch>
  ```
  ```bash
  git push --set-upstream origin <branch>
  ```
### pull
  ```bash
  git pull origin <branch>
  ```
## **STAGING**
### add
  ```bash
  git add .
  ```
  ```bash
  git add <file>
  ```

## **LOCAL**

  ```bash
  git commit -m "msg"
  ```
  ```bash
  git init
  ```



### Branching and Merging

- **List all branches**
  ```bash
  git branch
  ```

- **Create a new branch**
  ```bash
  git branch <branch-name>
  ```

- **Switch to a branch**
  ```bash
  git checkout [branch-name]
  ```

- **Merge a branch into the active branch**
  ```bash
  git merge [branch-name]
  ```

- **Delete a branch**
  ```bash
  git branch -d [branch-name]
  ```

## Stash

- **Stash changes**
  ```bash
  git stash
  ```

- **List stashed changes**
  ```bash
  git stash list
  ```

- **Apply stashed changes**
  ```bash
  git stash apply
  ```

## Checking Status and Logs

- **Check status**
  ```bash
  git status
  ```

- **View commit history**
  ```bash
  git log
  ```
