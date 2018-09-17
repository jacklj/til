### When trying to set git up to use an sshh key for pushing/pulling, rather than having to enter in your username/password each time. You've added the SSH key but git still asks for your credentials

`https://` URLs will always ask for a password (unless you configure a credential helper).

You need to use an SSH url instead, i.e. starting with `git@...`, e.g. `origin git@github.com:name/repo`

You change the url for an existing repo with `git remote set-url`, or edit the `.git/config` file directly (e.g. with VIM)

Then you should be able to git push origin <branch> without being asked for a password.
