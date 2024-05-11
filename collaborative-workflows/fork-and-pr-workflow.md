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

# Fork and PR Workflow

{% hint style="info" %}
This is the standard and recommended collaborative workflow by Github.
{% endhint %}

## What is forking?

Forking is the process of creating a at-the-time copy of a remote repository. So any branches and code from the original (called "upstream") repository.

You can create a fork of a repository by visiting the upstream repository link and selecting the "Fork" button:

<figure><img src="../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

## How does it works for collaboration?

Say your friend is working on the latest cutting edge project and you want to contribute some changes but you are not entirely sure how the codebase works. You can create a fork of your friend's repository, clone it locally, and play around with the codebase.

All of these changes will not be made available to your friend's repository as you have not made it explicit that they should be reflected on their repository.

:white\_check\_mark: Forking allows potential contributors to work on changes without directly affecting the original repository

:white\_check\_mark: Forks are stored under your account, not your friend's account

:white\_check\_mark: You can only make a single fork of a repository

## Workflow in action

Now that we have established what forking is about, let us now see this workflow in action.

First, create a fork of the demo repository: [https://github.com/woojiahao/new-folder/tree/main](https://github.com/woojiahao/new-folder/tree/main).

Then, clone the fork to your local machine and navigate to the folder:

```
git clone git@github.com:<your Github username>/new-folder.git fork-folder/
cd fork-folder/
```

Then, make a change to the repository like adding a new file, deleting something from `hello.txt`, etc.

Once done, commit those changes and push them to your fork.

```
git add .
git commit -m "fork changes"
git push origin main
```

Then, navigate back to the original repository and create a pull request. This time, you should notice that the `compare` (target branch) dropdown should include your fork's `main` branch as well.

Everything else is the same as described in [pull-requests-prs.md](pull-requests-prs.md "mention").&#x20;

Voila! You have now completed the fork and PR workflow. However, there are some caveats!

## What happens if my friend makes changes to the original repository?

In such scenarios, it is necessary to add a new remote (see [integrating-remote-repositories.md](../fundamental-concepts/integrating-remote-repositories.md "mention") for more information about this) pointing to the upstream repository.

To do so, you can run the following line (change the repository link where applicable):

```
git remote add upstream https://github.com/woojiahao/new-folder.git
```

Note that the URL used is the one under "HTTPS" since you do not have SSH access to the demo repository.

Once this `upstream` remote has been created, we can fetch any changes made to the original repository using the `git pull` command as such:

```
git pull upstream main
```

This will automatically fetch and merge any changes from the original repository to your local repository. However, if you want to have some more control over the merging process, you can use the following:

```
git fetch upstream main
git merge upstream/main
```

The first command retrieves the latest changes (but does not apply them locally). The second command performs a standard merge action, merging the changes from the upstream repository with your current local branch.

## Making PRs from forked branches

You can also create a remote branch on the fork and make a PR from that branch as the source branch instead. Just create a new branch locally for the fork and push it to your fork:

```
git checkout -b new-fork-branch
git push origin new-fork-branch
```
