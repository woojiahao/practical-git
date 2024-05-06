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

# Getting Started

To get a good grasp on Git, we will first focus our attentions on working with Git on [local repositories](fundamentals-of-git.md#local-and-remote-repositories).

## Creating a local repository

You can create a local repository from an existing project folder or from an empty folder. For the sake of simplicity, we opted to demonstrate the steps to create a local repository from scratch.

First, create the folder:

```
mkdir new-folder/
```

Then, navigate to the folder:

```
cd new-folder/
```

Finally, run the following command:

```
git init
```

This tells Git that you want this folder to be monitored by Git.

## Adding a new file

Create a new file in the folder and add some text to it.

```
echo 'Hello world' >> hello.txt
```

{% hint style="info" %}
The command above essentially redirects the output of the `echo` (Hello world) into a new file `hello.txt`
{% endhint %}

If you don't want to use bash commands, you can just create the file using your preferred method as well.

## Making your first commit

### Getting the status of a repository

Now, run the following command to view the status of your repository:

```
git status
```

You should see the following:

```
On branch main

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	hello.txt

nothing added to commit but untracked files present (use "git add" to track)
```

Recall that in [#adding-files-to-a-snapshot](fundamentals-of-git.md#adding-files-to-a-snapshot "mention"), Git does not automatically add files to a snapshot as it does not know exactly what you want. So we want to tell Git that we want `hello.txt` in the snapshot.

{% hint style="info" %}
`git status` is to view the state of your repository in Git's eyes. Use it to view things like the current files in the snapshot.
{% endhint %}

### Tracking files

You may notice that the `git status` message states that `hello.txt` is untracked. Untracked files are those that have never been registered with Git before. They are often new files that have been added to the repository and have not existed in any snapshots.

Files that have been added to a snapshot before are considered "tracked" and Git knows to look out for changes between snapshots.

### Adding files to the staging area

As discussed in [#introducing-the-commit](fundamentals-of-git.md#introducing-the-commit "mention"), a file from the working directory needs to be explicitly added to the staging area for a snapshot to include it. By default, an untracked file that is added to a snapshot becomes tracked for future snapshots.

To add `hello.txt` to the staging area, use the following command:

```
git add hello.txt
```

Then, use `git status` to view the status of your repository again:

```
On branch main

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
	new file:   hello.txt
```

Notice that now, instead of stating that your file is untracked, Git is indicating that the changes have not committed. This is a sign that the file(s) have been tracked and added to the snapshot.

{% hint style="info" %}
You can use `.` to add all files in the current folder as well.
{% endhint %}

### Taking the snapshot

Now, to take the snapshot (make the commit), you can use the following:

```
git commit -m "First commit"
```

The `-m` flag is used to specify the commit message. Every commit has an accompanying message that you can use to indicate what the commit contains/entails.

{% hint style="info" %}
If you do not use `-m`, your favorite terminal/GUI editor will be launched and you can compose the commit message in that editor, save it, and close the editor
{% endhint %}

There you have it! You have made a local repository and created a snapshot! We will now look at how we can integrate Github with your local repository!
