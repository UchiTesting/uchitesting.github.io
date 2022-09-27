GIT Commands
============


## GIT Log

| Command | Option | Description |
|-|-|-|
| `git log` |  | Displays the commit log |
|  | `--oneline` | Display commits on 1 line each |
|  | `--graph` | Shows a textual graph of the commits. Can be used along --oneline |
|  | `--stat` | Shows statistics about commits |
|  | `-p` | Shows actual changes. Not very convenient to watch such thing in a terminal |
|  | `-{n}` | Where n is how many lines we want to see. Can be used with --oneline |
|  | `--author="{authorName}"` | Lookup for specific author |
|  | `--grep="{expression}"` | Finds a string of text into commit log |
|  | `--pretty=format:"{formatString}"` | Formats the output string |
|  |  | **Commit** |
|  |  |  |
|  |  | *Hash* |
|  |  | `%H` 	commit hash |
|  |  | `%h` 	(abbrev) commit hash |
|  |  |  |
|  |  | **Tree** |
|  |  | `%T` 	tree hash |
|  |  | `%t` 	(abbrev) tree hash |
|  |  |  |
|  |  | *Parent* |
|  |  | `%P` 	parent hash |
|  |  | `%p` 	(abbrev) parent hash |
|  |  |  |
|  |  | **Commit** |
|  |  | `%s` 	commit subject |
|  |  | `%f` 	commit subject, filename style |
|  |  | `%b` 	commit body |
|  |  | `%d` 	ref names |
|  |  | `%e` 	encoding |
|  |  |  |
|  |  | **Author** |
|  |  |  |
|  |  | *Name* |
|  |  | `%an` 	author |
|  |  | `%aN` 	author, respecting mailmap |
|  |  |  |
|  |  | *Email* |
|  |  | `%ae` 	author email |
|  |  | `%aE` 	author email, respecting mailmap |
|  |  |  |
|  |  | *Date* |
|  |  | `%aD` 	author date (rfc2882) |
|  |  | `%ar` 	author date (relative) |
|  |  | `%at` 	author date (unix timestamp) |
|  |  | `%ai` 	author date (iso8601) |
|  |  |  |
|  |  | **Comitter** |
|  |  |  |
|  |  | *Name* |
|  |  | `%cn` 	committer name |
|  |  | `%cN` 	committer name, respecting mailmap |
|  |  |  |
|  |  | *Email* |
|  |  | `%ce` 	committer email |
|  |  | `%cE` 	committer email, respecting mailmap |
|  |  |  |
|  |  | *Date* |
|  |  | `%cD` 	committer date (rfc2882) |
|  |  | `%cr` 	committer date (relative) |
|  |  | `%ct` 	committer date (unix timestamp) |
|  |  | `%ci` 	committer date (iso8601) |
|  |  |  |
|  | `--merges` | Filter on merges |
|  | `--no-merges` | Filter out merges from the results |
| `git lg` |  | Similar to git log but gives more details such as commiter name and relative date informations |
| `git shortlog` |  | Shows commits grouped by commiter |
|  | `-n` | Sorts by commit count |
|  | `-s` | Summary. Used with -n |
|  | `-e` | Adds email information |


## GIT Reset

| Command | Option | Description |
|-|-|-|
| `git reset` |  |  |
|  | `--hard {commitHash}` | Puts the repository to the state of the selected commit |
|  | `--soft {commitHash}` | Only removes the last commit operation. Handy in case of typo |
|  | `--mixed {commitHash}` | Default behaviour. Removes the last commit and put any changed file as untracked |
|  | `HEAD~{n}` | Reset the last *n* commits in one go |
|  |  |  |

## GIT Revert and Amend

| Command | Option | Description |
|-|-|-|
| `git revert {commitHash}` |  | Reverts a specific commit. Better used only on the last commit or will likely lead to merge conflicts |
| `git commit` |  |  |
|  | `--amend -m "{newMessage}"` | Corrects last commit message |
|  | `--amend --author="{AuthorName} <{email}>"` | Corrects Author information |

## Cherry Picking

Copy a commit into another branch

| Command | Option | Description |
|-|-|-|
| `git cherry-pick	{commitHash}` |  |  |

Has to be performed in the receiving branch. Asks for the commit hash to be added as the last commit of the checkout (current) branch.
Automatically commits. Use --no-commit to prevent that.

## GIT Reflog

| Command | Option | Description |
|-|-|-|
| `git reflog` |  | Shows actions for main branch |
|  | `show {branch}` | Shows actions made in a specific branch |

## GIT Stash

Allows to create a temporary commit to prevent actually commiting. It has pointers in .git/refs/stash

| Command | Option | Description |
|-|-|-|
| `git stash` |  | Create a save state of the current branch |
|  | `pop` | Retrieves the stash commit in current branch |

## GIT Garbage collection

Performs GIT maintenance operation such as cleaning old references or pack repository.

| Command | Option | Description |
|-|-|-|
| `git gc` |  | Performs garbage collection |
