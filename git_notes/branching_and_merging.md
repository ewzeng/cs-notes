##### Branching

can branch from any commit

working directory can only reflect one branch at a time

detached HEAD = not at tip of a branch. thus if you want to commit, need to make a new branch

##### Merges

*when modifications in one branch do not conflict with modifications found in another branch, git computes a merge result and creates a new commit that represents the new, unified state. but when branches conflict, which occurs whenever changes compete to alter the same line of the same file, git does not resolve the dispute. instead, git marks such contentious changes as “unmerged” in the index and leaves reconciliation to you, the developer. when git cannot merge automatically, it’s also up to you to make the final commit once all conflicts are resolved.*