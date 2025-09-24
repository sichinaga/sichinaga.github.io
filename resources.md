---
layout: default
permalink: /resources/
title: Sara Ichinaga
---

# Resources

Table of Contents:
- [Helpful Code Snippets and Tips](#helpful-code-snippets-and-tips)
    - [Squishing multiple commits into one](#squishing-multiple-commits-into-one)
    - [Basic Anaconda environment building for Python](#basic-anaconda-environment-building-for-python)

## Helpful Code Snippets and Tips

### Squishing multiple commits into one
Credit: Isabella Heppe, my amazing partner who learned this from a senior developer during her time at Expedia Group.

**Step 1:** Run the following command to see the hash of every single commit that you have made so far. Note the hash of the commit that comes chronologically _right before_ the group of commits that you would like to collapse.
```bash
git log --oneline
```

**Step 2:** Perform an interactive rebase using the hash code from step 1. Enter editing mode in Vim and replace `pick` with `fixup` on all of the commits that you wish to collapse into your main commit. Make sure at least one commit (your main commit) still has `pick`.
```bash
git rebase -i <hash>
```

**Step 3:** Perform a force push to incorporate the commit history changes.
```bash
git push -f
```

### Basic Anaconda environment building for Python
Credit: Alex Hsu, my awesome colleague who helped me do this after many years of me using extremely unorganized Python environments.

**Step 1:**
```bash
conda create --name <name>
```
```bash
conda activate <name>
```
```bash
conda install python
```

**Step 2:**
```bash
conda install ipython
conda install jupyter
```
```bash
python -m pip install <packages>
```