* ## What is the difference between git fetch and git pull?
  * `git fetch` downloads the changes from the remote repository but does not merge them with your local repository. 
  * `git merge` merges the changes from the remote repository with your local repository.
  * `git pull` is a combination of `git fetch` and `git merge`.

* ## What is the git rebase?
`git rebase` is used to reapply commits on top of another base tip. It is used to maintain a linear project history.

* ## What is the difference between git rebase and git merge?
  * `git rebase` rewrites the commit history by creating new commits for each commit in the original branch. 
  * `git merge` merges the changes from one branch to another branch.

* ## What is the git cherry-pick?

`git cherry-pick` is used to apply a commit from one branch to another branch.

* ## What is the git stash?

`git stash` is used to save the changes in the working directory and index to a stack. It is used to switch to another branch without committing the changes.

* ## What is the git bisect?

`git bisect` is used to find the commit that introduced a bug by performing a binary search between two commits.

* ## What is the git tag?

`git tag` is used to create a tag for a specific commit. It is used to mark a specific commit in the repository.

* ## What is the git blame?

`git blame` is used to view the author and commit information for each line in a file. It shows the commit that last modified each line in the file.

* ## What is the git log?

`git log` is used to view the commit history of a repository. It shows the commit messages, authors, dates, and commit hashes.

* ## What is the git reset?

`git reset` is used to reset the current HEAD to a specific state. It is used to undo changes in the working directory and index.

type of reset commands:
  * `git reset --soft` : Moves HEAD back to the specified commit, undo all the changes made between where HEAD was pointing and the specified commit.
  * `git reset --hard` : Reset the current branch to a previous commit, discarding any local changes and modifications made to the files.

