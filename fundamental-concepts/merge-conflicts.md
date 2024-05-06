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

<figure><img src="../.gitbook/assets/image.png" alt="" width="563"><figcaption></figcaption></figure>

To make this more concrete, let's fabricate a merge conflict.

Firstly, create a new branch&#x20;
