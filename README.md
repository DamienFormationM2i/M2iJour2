# M2iJour2
For the patch

Use git stash when you want to record the current state of the working directory and the index, but want to go back to a clean working directory. The command saves your local modifications away and reverts the working directory to match the HEAD commit.

The modifications stashed away by this command can be listed with git stash list, inspected with git stash show, and restored (potentially on top of a different commit) with git stash apply. Calling git stash without any arguments is equivalent to git stash push. A stash is by default listed as "WIP on branchname …​", but you can give a more descriptive message on the command line when you create one.

The latest stash you created is stored in refs/stash; older stashes are found in the reflog of this reference and can be named using the usual reflog syntax (e.g. stash@{0} is the most recently created stash, stash@{1} is the one before it, stash@{2.hours.ago} is also possible). Stashes may also be referenced by specifying just the stash index (e.g. the integer n is equivalent to stash@{n}).

Given one or more existing commits, apply the change each one introduces, recording a new commit for each. This requires your working tree to be clean (no modifications from the HEAD commit).

When it is not obvious how to apply a change, the following happens:

    The current branch and HEAD pointer stay at the last commit successfully made.

    The CHERRY_PICK_HEAD ref is set to point at the commit that introduced the change that is difficult to apply.

    Paths in which the change applied cleanly are updated both in the index file and in your working tree.

    For conflicting paths, the index file records up to three versions, as described in the "TRUE MERGE" section of git-merge(1). The working tree files will include a description of the conflict bracketed by the usual conflict markers <<<<<<< and >>>>>>>.

    No other modifications are made.

See git-merge(1) for some hints on resolving such conflicts.
