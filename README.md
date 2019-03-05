# git-project-migration（GIt项目迁移流程）

### 1 Clone old project.
```shell
git clone {old project address} // myoldProject
```
### 2 Cd myoldProject.
```shell
cd myoldProject
```

### 3 Checkout all branch from origin remote.
```shell
git branch -r | grep -v '\->' | while read remote; do git branch --track "${remote#origin/}" "$remote"; done
git fetch --all
git pull -all
```
### 4 Add new preject remote address and backups the old.
```shell
git remote rename origin old-origin
git remote add origin {new project address}
```
##### Can also edit the git config file to change remote address:
```shell
cd myoldProject
```
```shell
vi ./.git/config
```
```text
edit the url under '[remote "origin"]' to the new project address
```
```text
that is ok!
```

### 5 Push all .
```shell
git push -u origin --all
```
### 6 Check your project has migration completed.
