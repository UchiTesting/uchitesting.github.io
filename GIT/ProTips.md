Pro Tips
========


## Dealing with branches

### Maintaing branches

#### Deletetion

Branches deleted on the remote (after a merge request, manually deleted, ...) can be pruned in different manners

`git fetch --prune`, `git pull --prune` or `git remote prune origin`

They differ in the output they provide, yet basically gets to the same result.
The references to remote branches will be removed.
However local branches remain. We need an extra step to clean the local branches that once had a remote.

`git branch -vv | awk '/: gone]/{print $1}' | xargs -r git branch -d`

A dry run can be obtained by simply not piping to `xargs`.

If the branch never had a remote then simply delete the branch using `-D` switch on `git branch`.
`-d` would check if the remote got merged and will display a message warning about it.

`git branch -D my-safe-to-delete-branch`

### Getting intel about branches

#### Knowing the branch origin

Many possibilities but one that is straight to the point is `git reflog`.
It usually states the origin branch to some given branch

```bash
$ git reflog lib-wip
0af639c (HEAD -> lib-wip, origin/lib-wip) lib-wip@{0}: commit: Add test to check amount formatting against invariant culture
682587a (lib-dev) lib-wip@{1}: branch: Created from lib-dev
```

There are other ways to investigate such matter but I'm currently still investig the available investigation tools. Stay tuned. ;) (Upcoming commit in XXII century)