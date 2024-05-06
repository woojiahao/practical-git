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

# Fundamentals of Git

Let us first understand some of the key terminologies and ideas behind Git to help improve your intuition of Git.

## What is Git?

Git is a [version control system](https://www.atlassian.com/git/tutorials/what-is-version-control) first created by Linus Torvalds with the aim of managing software changes over time. It is not the first version control system (SVN and Mercurial existed before it) but it is one of the most commonly used ones.

At a high level, version control systems track the "history of changes" of a piece of software over time. Git, in particular, emphasizes the use of a decentralized collaborative workflow, allowing teams to collaborate and work on a codebase without an active connection to the centralized repository.

## Local and remote repositories

Git relies on the core concept of a repository, which is essentially a parent folder that Git is added to to monitor the changes of the folder and its contents (including sub-folders).

These repositories can exist on both your local machines or remotely on an external server (or [self-hosted](https://about.gitea.com/)). This guide will look at both instances.

Github is an example of a hosted remote Git server where you can create remote repositories and work on them locally (while pushing changes remotely, hence the "decentralized" nature of Git).1

## Introducing the \`\`commit"

To track a codebase, Git relies on a system of **commits.**

You can think of a commit as a _snapshot_ of the instance of the codebase at a given point in time. For instance, when you are fixing a bug or implementing a new feature, you may want to save the current state of the codebase (take a snapshot). Every time you take a snapshot, it gets added over the previous snapshot as a set of changes that were introduced in the new version of the codebase.

Internally, Git tracks these commits by creating an [Directed Acyclic Graph (DAG)](https://en.wikipedia.org/wiki/Directed\_acyclic\_graph), with every commit representing a node in the graph and every edge points back to the previous commit that occurred.

<figure><img src="../.gitbook/assets/image (3).png" alt="" width="331"><figcaption></figcaption></figure>

You may notice that each commit node may have more than one incoming edge. This is where the idea of **branching** stems from.

## Branching

Suppose that you were working on some changes when a bug report comes in and you have to urgently fix it. You don't know if the bug fix works immediately so you don't want to work on the bug fix in the same location where you're working on your changes. This is when branching comes in handy.

Unofficially, you can try thinking of a branch as an independent line of work that stems (or branches off) from a point in development. They can be seen by the nodes `C2 <- C3 <- C5` in the previous diagram. They let you work on features or bug fixes without interfering with the current set of changes.

By default, Git starts out with a `main` branch.

## Adding files to a snapshot

By default, Git does not know what files it should be including in a snapshot (and this is a good thing because we don't want Git to just add every file as they may contain sensitive information).

This is where the "three areas" concept comes into play. It is often good to think of your projects with Git as three separate concepts:

<figure><img src="../.gitbook/assets/areas.png" alt="" width="563"><figcaption></figcaption></figure>

1. Working directory: where your codebase actually resides
2. Staging area: set of files that you want to include in a snapshot
3. Repository: local/remote repository storing metadata about the project and Git

By default, all of your files reside in the working directory and are not yet added to the staging area. If you want a file included in the staging area, then you must first add it to the staging area (we will cover how this happens later on).

{% hint style="info" %}
There are also ways to remove files from the staging area!
{% endhint %}

