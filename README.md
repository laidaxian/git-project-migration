# git-project-migration
GIt项目迁移流程

1 Clone old project.
# git clone {old project address} // myoldProject

2 cd myoldProject.

3 Checkout all branch from origin remote.
# git branch -r | grep -v '\->' | while read remote; do git branch --track "${remote#origin/}" "$remote"; done
# git fetch --all
# git pull -all

4 Add new preject remote address and backups the old.
# git remote rename origin old-origin
# git remote add origin {new project address}
  (* Can also edit the git config file to change remote address:
     1 # cd myoldProject
     2 # vi ./.git/config
     3 edit the url under '[remote "origin"]' to the new project address
     4 that is ok!
  )

5 push all .
# git push -u origin --all

6 check your project has migration completed.
