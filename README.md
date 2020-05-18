# Learning about Sub Modules

This is a test repo to learn about git submodules, following steps from https://git-scm.com/book/en/v2/Git-Tools-Submodules

## Adding a submodule
---

### Pick repo URL and Add
```
git submodule add https://github.com/mochajs/mocha.git
```
Running the `git submodule add` command with the URL of the repository your want to add, works similarly to `git clone` as by default it will create the directory with that repo's content at the same path from where you run the command. However you can add a custom path after the URL. `git submodule add https://github.com/mochajs/mocha.git [PATH_TO_NEW_LOCATION_FOR_MODULE]`

### Check status and diff
```
git status
``` 
shows that the submodule and new `.gitmodules` file are already staged and ready to commit to the project git. 

```
git diff --cached mocha
``` 
shows that the project is at a particular git commit (the same commit hash from the project when it was added as a submodule) 

## Pulling Project with submodule
---
### Clone Repository with empty submodules
```
git clone [URL_OF_MAIN_PROJECT_REPO]
``` 
is the typical command to add the project to your local computer, but it will display empty directories for the submodules. (in VS Code, it'll show an S indicator next to the directory name in the file tree).

### Setup submodules in cloned project
Perhaps you've cloned the project not realizing there are submodules in it.
```
git submodule update --init --recursive
``` 
is what you use to download the submodule contents into their respective directories, at the same checkout point referenced in the main project. According to the [docs](https://git-scm.com/book/en/v2/Git-Tools-Submodules#_cloning_submodules), without the `--recursive` flag, it will not include the submodules within submodules

### How to clone with submodule contents
```
git clone [URL_OF_MAIN_PROJECT_REPO] --recurse-submodules
``` 
Will initialize and update each submodule and any nested submodules (if the submodules also have submodules)

### Submodule out-of-sync
Your local submodule is out of date with the one on the MAIN_PROJECT_REPO. `git pull` **will not** update submodule files, it will only `fetch` the updates. using `git status` will show the latest changes to the submodules