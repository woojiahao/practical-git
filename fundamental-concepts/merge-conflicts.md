---
layout:
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# Merge Conflicts

Merge conflicts occurs when two (or more) modifications (made by yourself or others) are made to the same line of a file. This causes a state of confusion as Git is unsure which change should be applied. So rather than making a decision for you, it "errors" and lets you decide.

<figure><img src="../.gitbook/assets/image (10).png" alt="" width="563"><figcaption></figcaption></figure>

To make this more concrete, let's fabricate a merge conflict.

## Simulating a merge conflict

Firstly, create two new branches from `main`:

```
git checkout -b branch-A
git checkout main
git checkout -b branch-B
```

Then, on `branch-A`, edit the line `Hello World` by changing it (e.g. `Hello`). Remember to commit the changes!

```
git checkout branch-A
vim hello.txt
git add hello.txt
git commit -m "branch A changes"
```

Then, on `branch-B`, perform another edit on the same line but to a different text (e.g. `Hello Universe`)

```
git checkout branch-B
vim hello.txt
git add hello.txt
git commit -m "branch B changes"
```

Finally, switch back to `main` and merge both `branch-A` and `branch-B` together:

```
git checkout main
git merge branch-A
git merge branch-B
```

Merging `branch-A` should not have any issues but merging `branch-B` will have the following error:

```
Auto-merging hello.txt
CONFLICT (content): Merge conflict in hello.txt
Automatic merge failed; fix conflicts and then commit the result.
```

This means that Git is not entirely sure if it should keep the changes from `branch-A` or the changes from `branch-B` so it lets you decide.

You can use `git status` to view the state of the repository now that it has a merge conflict:

```
On branch main
Your branch is ahead of 'origin/main' by 1 commit.
  (use "git push" to publish your local commits)

You have unmerged paths.
  (fix conflicts and run "git commit")
  (use "git merge --abort" to abort the merge)

Unmerged paths:
  (use "git add <file>..." to mark resolution)
	both modified:   hello.txt

no changes added to commit (use "git add" and/or "git commit -a")
```

Notice that it indicates that `hello.txt` is unmerged. Only files with merge conflicts are left in this area. Any other files without a merge conflict will be merged as per usual.

## Resolving the merge conflict

To resolve the merge conflict, open up `hello.txt` in your favorite text editor.

You will notice the following (or something similar depending on your changes):

```
<<<<<<< HEAD
Hello
=======
Hello universe
>>>>>>> branch-B
```

Git displays both changes (delineated by the `======`) and all you need to do is to edit the area to remove the `<<<<<<< HEAD`, `=======`, and `>>>>>>> branch-B`. You may choose to delete the content in the top half, bottom half, both halves, or keep both.

Notice that the top half is the current content in the branch and the bottom half is the content that is about to be merged.

For the sake of simplicity, let's keep both changing by only removing the new lines:

```
Hello
Hello universe
```

Then, save the file and close the file. Then, add the file to the staging area:

```
git add hello.txt
```

Now, you can perform `git status` once more to view the status:

```
On branch main
Your branch is ahead of 'origin/main' by 1 commit.
  (use "git push" to publish your local commits)

All conflicts fixed but you are still merging.
  (use "git commit" to conclude merge)

Changes to be committed:
	modified:   hello.txt
```

The issue has been resolved and so Git no longer has a dedicated section for the unmerged files.

Finally, complete the merge by using `git commit`. You may notice that the commit message is already provided for you so you can just accept it as it is.

And there you have it, we have successfully caused and resolved a merge conflict! Now, onto the collaborative workflows that Git allows.
