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

# Setup

{% hint style="danger" %}
It is very important that these steps are done correctly to ensure that you can follow along.
{% endhint %}

To follow along this guide, you need to install the following:

1. [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)

To ensure that everything is working, run the following commands:

```
git version
```

You should see text like this:

```
git version 2.42.0
```

Once Git is setup on your local machine, do some initial configuration:

```
git config --global user.email "<your email>"
```

```
git config -- global user.name "<your name>"
```

Then, setup Github as such:

1. Create a [new Github account](https://docs.github.com/en/get-started/start-your-journey/creating-an-account-on-github)
2. Connecting to [Github with SSH](https://docs.github.com/en/authentication/connecting-to-github-with-ssh)
   1. Generate a new SSH key
   2. Add the SSH key to Github

To verify that Github is working, refer to [this guide](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/testing-your-ssh-connection?platform=mac) and run the given command (`ssh -T git@github.com`) to ensure that your SSH connection is working correctly.
