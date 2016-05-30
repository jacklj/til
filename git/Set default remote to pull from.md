git config branch.master.remote remote_branch_name
git config branch.master.merge refs/heads/master

This tells git:
1. when you're on the master branch, the default remote is remote_branch_name
2. when using git pull on master branch, with no remote and branch specified, use the default 
remote (remote_branch_name) and merge in the changes from the master branch


alternatively, edit the repo's Git config file (.git/config):
[branch "master"]
    remote = remote_branch_name
    merge = refs/heads/master
