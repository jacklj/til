Rerere remembers merge conflict resolutions (even from aborted merges / deleted merge commits).

Sometimes they're incorrect, so you can use `git rerere forget <file_name>` to forget the resolutions for that file.

Sometimes I need to start again with my merges and sometimes I'll not want what rerere remembers. 
Sometimes even git rerere forget isn't drastic enough. 
The following will clear the rerere cache:

`rm -rf .git/rr-cache`
