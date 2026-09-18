Git Team Sync Workflow

1. What did the rejected push error message tell you, and why did it happen?

The rejected push message told me that the remote repository contained commits that my local branch did not have. This happened because the two clones had diverged from the same starting commit. In Task 2, Clone A pushed the VIP bonus change to GitHub while Clone B was still working from the older version of the branch. Clone B then created its own commit for rounding loyalty points and tried to push it, but Git rejected the push because doing so without first integrating the remote changes could overwrite history.

2. What is the actual difference between how you resolved Task 3 (merge) vs Task 4 (rebase)?

In Task 3, I used `git fetch` followed by `git merge`. Git combined the two branches and created a merge commit after I manually resolved the conflict in `calculateLoyaltyPoints`. Both developers' changes remained in the history as separate lines of development that were joined by the merge.

In Task 4, I used `git fetch` followed by `git rebase`. Instead of creating another merge commit, Git replayed my local commit on top of the updated remote branch. I still had to manually resolve a conflict because the changes affected the same function. After resolving it, I used `git rebase --continue` instead of creating a normal commit myself. The result was a more linear history.

3. What one habit would have avoided both rejected pushes in this lab?

One habit that would have avoided both rejected pushes is updating my local branch before starting new work. Fetching the latest remote changes before making a commit helps ensure that I am working from the current version of the shared branch. This reduces the chance of creating a divergent branch based on outdated information.

4. Which approach - merge or rebase - would you default to on a shared team branch, and why?

I would choose between merge and rebase based on the team's Git workflow and whether the commits have already been shared. Merge preserves the existing history and does not rewrite commits, which can make it appropriate when integrating work that is already shared. Rebase can create a more linear history and can be useful for local or private work before it is shared. For a shared branch, I would follow the team's established policy rather than using rebase automatically, especially because rebasing commits that other developers already depend on can cause confusion.