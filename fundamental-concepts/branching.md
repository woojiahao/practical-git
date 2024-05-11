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

# Branching

As mentioned in [#branching](fundamentals-of-git.md#branching "mention"), branches can be thought of as independent lines of work that allow you to work on features/bug fixes independently from the `main` branch. This means that any changes made on a branch is not reflected on the `main` branch UNTIL otherwise specified.

This is very powerful in allowing you to separate your work from the primary branch for development or just from other people's work.

For simplicity in this section, we will focus on the bare basics of branching in Git.

## HEAD

Notice that all commits come with a unique ID. This can make it difficult to reference the exact commit you are on. This is where `HEAD` comes in.

`HEAD` is a special name given to the latest commit of your current branch. It is a nice syntactic sugar to allow you to easily reference the latest commit without knowing its exact commit ID.

<figure><img src="../.gitbook/assets/image (1) (1).png" alt="" width="563"><figcaption></figcaption></figure>

## Creating a new branch

By default, a new branch is always created from the point of `HEAD` of your current branch (usually `main`) onwards. This means that the branch will have all the snapshots that precede (and include) `HEAD` but any new snapshots made on the branch are not reflected (yet) on `main.`

There are two ways to create a new branch:

```
git branch <branch name>
```

Then, you can switch to the branch by using:

```
git checkout <branch name>
```

Alternatively, you can use the `git checkout` command for both:

```
git checkout -b <branch name>
```

## Changing branches

As mentioned earlier, you can switch to a branch via:

```
git checkout <branch name>
```

## Viewing all branches created

To view all branches, you can use the following:

```
git branch -v
```

## Deleting a branch

To delete a branch, you add the `-d` flag:

```
git branch -d <branch name>
```

## Renaming a branch

You may have misspelled the branch name or parts of it. You can rectify it using the `-m` flag:

```
git branch -m <new branch name>
```

{% hint style="info" %}
This renames the current branch that you are on.
{% endhint %}

## Combining changes of branches

Recall that we mentioned that the changes of a branch are not reflected across any other branch UNTIL otherwise specified? How exactly do we specify this?

An easy way to do so is by merging the branches into one another.

Suppose we have two branches: `main` and `feature-A` and we want all the changes from `feature-A` to be present in `main` so that we can demo it to the executives. We first need to clearly denote which is the source branch (where the changes exist) and the target branch (where we want the changes to appear in). In this scenario, `feature-A` is the source branch and `main` is the target branch.

Then, a simple procedure to perform the merge would be:

1. Switch to the target branch
2. Merge source branch into target branch

This can be done via:

```
git checkout main
git merge feature-A
```

However, this process is not always so straightforward. As you will see in the coming chapter, merging has its own set of "problems" that may arise.
