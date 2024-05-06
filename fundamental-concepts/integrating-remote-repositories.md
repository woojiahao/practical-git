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

# Integrating Remote Repositories

&#x20;Now that we have started working on our local repository in [getting-started.md](getting-started.md "mention"), we may want others to view the contents of our repositories. We may also want a layer of security against local machine crashes by storing our repositories somewhere else.&#x20;

This is where remote repositories and Github come into play.&#x20;

## Creating a Github repository

{% hint style="warning" %}
As per [setup.md](../setup.md "mention"), you should already have setup Github and SSH. If not, please go to [setup.md](../setup.md "mention") to ensure that it everything works before proceeding as the remainder of the guide will be using Github.
{% endhint %}

You can visit the following link: [https://github.com/new](https://github.com/new) or simply use the Github UI to create a new repository:

<figure><img src="../.gitbook/assets/Screenshot 2024-05-06 at 14.44.39.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/Screenshot 2024-05-06 at 14.45.28.png" alt="" width="289"><figcaption></figcaption></figure>

Then, you should see the following page:

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

Some key details to take note of:

* Repository template: creates a project with some basic files already included (we won't use this)
* Repository name: any name you want to give your project, you can follow the same name as your local folder <mark style="background-color:green;">**(please fill this up)**</mark>
* Description: optional description about your project (optional)
* Visibility: public (publicly accessible and viewable) or private (only viewable to yourself and any [collaborators](https://docs.github.com/en/account-and-profile/setting-up-and-managing-your-personal-account-on-github/managing-access-to-your-personal-repositories/inviting-collaborators-to-a-personal-repository)) <mark style="background-color:green;">**(set it to public for now)**</mark>
* `README`: file that normally contains basic documentation about the project <mark style="background-color:red;">**(do not create one)**</mark>
* `.gitignore`: tells Git to ignore certain files (such as private files) <mark style="background-color:red;">**(do not create one)**</mark>
* `LICENSE`: specifies an open-source license (if any) <mark style="background-color:red;">**(do not create one)**</mark>

{% hint style="danger" %}
We do not create a `README` or `.gitignore` or `LICENSE` as we have existing files locally and we don't want to cause any problems when trying to move the local repository to Github.
{% endhint %}

Once done, you should see the following:

<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

## Connecting your local repository with the remote repository

Now, let's get your local repository to Github through the remote repository you just created.

{% hint style="info" %}
We will be following the instructions under the "...or push an existing repository from the command line" section of the Github repository.
{% endhint %}

### Adding a new remote

The local repository needs to know which remote repository it is going to be connected to. This is where the `git remote` command comes in handy.

It is used to manage remote repositories for your local repository.

In this instance, we want to add the remote repository you created to the local repository under the name `origin` (in fact, we can name it anything, `origin` is just the convention):

```
git remote add origin git@github.com:<github username>/<repository name>.git
```

### Retrieving a remote branch

Now that you have added the remote repository link to the local repository, you then need to retrieve the `main` branch from the remote repository (recall that the `main`  branch is the default branch).

This is done using&#x20;

```
git branch -M main
```

### Uploading local repository snapshots to remote repository

To upload all local snapshots to the remote repository, you will use `git push`.

```
git push -u origin main
```

{% hint style="info" %}
`-u` flag will set the "[upstream](https://web.archive.org/web/20200307113003/https://mislav.net/2010/07/git-tips/)" which refers to the default remote repository you would want to push and pull from. Subsequent calls to `git push` will not require `-u`.
{% endhint %}

Once done, you can navigate back to the Github repository and refresh the page. You will notice the following:

<figure><img src="../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

If you open `hello.txt`, you'll also see that it has `Hello World` in it.

## Another way to use remote repositories

What you have just accomplished is the "push" workflow where you push an existing local repository to Github. However, there may be times where you want to create a remote repository first and use it locally. This can be done via the "pull" workflow or "clone" workflow.

We will be working off of the same Github repository. Suppose that you want to create a copy of the remote repository on your local machine. You can do so with the following.

Ensure that you navigate out of the current folder:

```
cd ../
```

Then, use the `git clone` command:

```
git clone git@github.com:<github username>/<repository name>.git another-folder/
```

{% hint style="info" %}
The `another-folder/` at the end is crucial as it tells Git to create a copy of the remote repository but store it under a different folder name (other than `<repository name>`)
{% endhint %}

Then, you can navigate into the folder and view `hello.txt`:

```
cd another-folder/
cat hello.txt
```

Regardless of the method you have used, you have now integrated a local repository with a remote one! Let's move on to the final fundamental concept: merge conflicts.
