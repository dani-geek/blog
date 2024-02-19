---
layout: post
title: The complicated way to update a forked repo
date: 2021-01-29 01:00 +0700
modified: 2021-03-07 16:49:47 +07:00
description: There are two ways to update the forked repository using the web interface provided by github but it is complicated, or through the terminal which is even more complicated.
tag:
  - tips
  - git
  - software
image: /cara-memperbarui-fork-repository/repo.png
---

It all started when I wanted to update an old repo from an organization, the intention was to rework it, it turned out that from the original repo there was an update, as well as making an article deh, more or less the picture is like this.

<figure>
<img src="{{ page.image }}" alt="ilustrasi repo yang mau diupdate">
<figcaption>Fig 1. A picture of the complexity.</figcaption>
</figure>

There are two ways to update the forked repository using the web interface provided by github but it is complicated, or through the terminal which is even more complicated.

### Through Github (boring way) 💻

1. Open the forked repo on Github.
1. Click **Pull Requests** on the right, then **New Pull Request**.
1. It will bring up the result of the compare between the upstream repo and your repo (forked repo), and if it states "There isn't anything to compare.", press the **switching the base** link, which now your repo (forked repo) will be flipped to the base repo and the upstream repo to the head repo.
1. Press **Create Pull Request**, give the pull request a title, Press **Send Pull Request**.
1. Press **Merge Pull Request** and **Confirm Merge**.

\* _make sure you don't change anything in the forked repo, so that it merges automatically, otherwise it's a conflict at best._

### Through terminal ⌨️

Add the original remote repository address here not named `upstream`, replace `ORIGINAL_OWNER` and `ORIGINAL_REPO` with your original repo address.

```bash
$ git add remote upstream git@github.com:ORIGINAL_OWNER/ORIGINAL_REPO.git
$ git remote -v
> origin    git@github.com:piharpi/www.git (fetch) # forked repo
> origin    git@github.com:piharpi/www.git (push) # forked repo
> upstream    git@github.com:ORIGINAL_OWNER/ORIGINAL_REPO.git (fetch) # upstream repo / original repo
> upstream    git@github.com:ORIGINAL_OWNER/ORIGINAL_REPO.git (push) # upstream repo / original repo
```

Checkout to local branch `master`.

```bash
$ git checkout master
> Switched to branch 'master'
```

If so, Merge local repo with remote `upstream/master`.

```bash
$ git merge upstream/master
```

Finally push the local repo to the remote `origin`.

```bash
$ git add -A
$ git commit -m "updating origin repo" && git push -u origin master
```

Good luck with this complicated method, hopefully it can be understood, I myself prefer to go through the terminal, if there is something complicated why look for something easy.

##### Resources

- [Syncing a fork](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/syncing-a-fork)
- [Update your fork directly on Github](https://rick.cogley.info/post/update-your-forked-repository-directly-on-github/#top)
