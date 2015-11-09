---
layout: post
title: Delete commits from a branch in Git
---

**Careful:** `git reset --hard` *WILL DELETE YOUR WORKING DIRECTORY CHANGES.* Be sure to **stash any local changes you want to keep** before running this command.

<!--break-->

Assuming you are sitting on that commit, then this command will wack it...

```bash
git reset --hard HEAD~1
```

The `HEAD~1` means the commit before head.

Or, you could look at the output of `git log`, find the commit id of the commit you want to back up to, and then do this:

```bash
git reset --hard <sha1-commit-id>
```

If you already pushed it, you will need to do a force push to get rid of it...

```bash
git push origin HEAD --force
```

**However**, if others may have pulled it, then you would be better off starting a new branch. Because when they pull, it will just merge it into their work, and you will get it pushed back up again.

If you already pushed, it may be better to use `git revert`, to create a "mirror image" commit that will undo the changes. However, both commits will both be in the log.

FYI `-- git reset --hard HEAD` is great if you want to get rid of WORK IN PROGRESS. It will reset you back to the most recent commit, and erase all the changes in your working tree and index.

Lastly, if you need to find a commit that you "deleted", it is typically present in `git reflog` unless you have garbage collected your repository.

Origin post [http://stackoverflow.com/questions/1338728/delete-commits-from-a-branch-in-git](http://stackoverflow.com/questions/1338728/delete-commits-from-a-branch-in-git)