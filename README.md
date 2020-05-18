# Learning about Sub Modules

This is a test repo to learn about git submodules, following steps from https://git-scm.com/book/en/v2/Git-Tools-Submodules

## Adding a submodule

### Pick repo URL and Add
`git submodule add https://github.com/mochajs/mocha.git`
Running the `git submodule add` command with the URL of the repository your want to add, works similarly to `git clone` as by default it will create the directory with that repo's content at the same path from where you run the command. However you can add a custom path after the URL. `git submodule add https://github.com/mochajs/mocha.git [PATH_TO_NEW_LOCATION_FOR_MODULE]`

### Check status and diff
`git status` shows that the submodule and new `.gitmodules` file are already staged and ready to commit to the project git. However, `git diff --cached mocha` shows that the project is at a particular git commit (the same commit hash from the project when it was added as a submodule) 