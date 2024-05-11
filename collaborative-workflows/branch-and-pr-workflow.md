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

# Branch and PR Workflow

While the [fork-and-pr-workflow.md](fork-and-pr-workflow.md "mention") is the recommended workflow, you could also work collaboratively by creating PRs through the original repository (i.e. no forks involved).

This may be simpler to setup for smaller projects (like Orbital), but we still highly recommend following the [fork-and-pr-workflow.md](fork-and-pr-workflow.md "mention") instead.

This workflow is very straightforward:

1. Clone the original repository
2. Create a local branch
3. Make changes to the local branch
4. Push the local branch to the original repository
5. Make a PR from the local branch to the `main` branch

While it is very simple, it is also very error prone as pushing directly to the original repository may result in directly overriding changes in the original repository if you are not careful and you may not even have the permissions to push directly to the original repository (this is the case for most open-source projects).
