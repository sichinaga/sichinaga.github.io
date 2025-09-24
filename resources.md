---
layout: default
permalink: /resources/
title: Sara Ichinaga
---

<center>
  <h1>Resources</h1>
</center>

Table of Contents:
- [Teaching Resources](#teaching-resources)
    - [T.1](#building-a-gradescope-autograder-with-gspack) Building a Gradescope autograder with gspack
- [Coding Resources](#coding-resources)
    - [C.1](#squishing-multiple-commits-into-one) Squishing multiple commits into one
    - [C.2](#basic-anaconda-environment-building) Basic Anaconda environment building

## Teaching Resources
I spent a long time trying to figure some of this out. Hopefully this helps you (that includes you future Sara).

### Building a Gradescope autograder with gspack
```
pip install -e .
```

## Coding Resources
Helpful code snippets that I tend to forget, and that I need written down.

### Squishing multiple commits into one
**Credit:** Isabella Heppe, my amazing partner who learned this from a senior developer during her time at Expedia Group.

**Step 1:** Run the following command to see the hash of every single commit that you have made so far. Note the hash of the commit that comes chronologically _right before_ the group of commits that you would like to collapse.
```
git log --oneline
```

**Step 2:** Perform an interactive rebase using the hash code from step 1. Enter editing mode in Vim and replace `pick` with `fixup` on all of the commits that you wish to collapse into your main commit. Make sure at least one commit (your main commit) still has `pick`.
```
git rebase -i <hash>
```

**Step 3:** Perform a force push to incorporate the commit history changes.
```
git push -f
```

### Basic Anaconda environment building
**Credit:** Alex Hsu, my awesome colleague who helped me do this after many many years of me using extremely unorganized Python environments.

**Step 1:**
```
conda create --name <name>
```
```
conda activate <name>
```
```
conda install python
```

**Step 2:**
```
conda install ipython
conda install jupyter
```
```
python -m pip install <packages>
```
