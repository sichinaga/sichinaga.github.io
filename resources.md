---
layout: default
permalink: /resources/
title: Sara Ichinaga
---

<center>
  <h1>Resources</h1>
</center>

Welcome to the resources page! This is where I document useful pieces of information that I tend to forget. A lot of this is here so that I can help my future self remember these things and avoid tirelessly re-teaching myself, but my hope is that these resources will be helpful to you too!

## Table of Contents:
- [Resources for Teaching](#resources-for-teaching)
    - [T.1](#t1-building-a-gradescope-autograder-with-gspack) Building a Gradescope autograder with gspack
- [Resources for Coding](#resources-for-coding)
    - [C.1](#c1-squishing-multiple-commits-into-one) Squishing multiple commits into one
    - [C.2](#c2-basic-anaconda-environment-building) Basic Anaconda environment building

## Resources for Teaching

### T.1. Building a Gradescope autograder with gspack
[gspack](https://github.com/aksholokhov/gspack) is a nifty set of code that helps streamline the process of building an autograder for coding assignments in Gradescope. The developers of the package have already done a fantastic job at explaining the details of their package, so I highly recommend that you start by reading the gspack README first.

Of course, you are probably here because you have indeed read the README and are still confused, that or you read it at some point and really don't want to figure the whole process out again. Assuming that you are new to building autograders, or you simply need a referesher, let me start by breaking down the most important things you need to know.

**How do I import and start using gspack?**

This is quite possibly my most important tip regarding gspack use and this is more likely than not the cause of almost everyone's issues with gspack but:

**TIP: INSTALL DIRECTLY FROM THE SOURCE!**

The last PyPI release of gspack was quite a while ago (as of writing this, it was 2022), so simply calling `pip install gspack` like the README suggests will leave you with an outdated version of gspack that will break the autograder build inside Gradescope. The actual source code in gspack however is quite up-to-date, so you might save yourself a few hours of debugging if you simply start with the source code and proceed from there.

To do this, I recommend that you perform an [editable installation](https://setuptools.pypa.io/en/latest/userguide/development_mode.html) of the package. Simply clone the source code from GitHub,

```shell
git clone https://github.com/aksholokhov/gspack.git
```

change directories to the folder you just cloned,

```shell
cd path-to-gspack-folder
```

and perform an editable pip installation from inside the cloned directory.

```shell
pip install -e .
```

If you still find that you are experiencing issues with you current installation of gspack, I recommend that you keep the following files in mind as you debug. Note: this list might _not_ be exhaustive!
- `gspack/requirements.txt`: Make sure all requirements are up-to-date.
- `gspack/src/gspack/templates/setup.sh`: Ensure that the calls to python, the pip installations, etc. are up-to-date.

**What files do I actually need?**

When using gspack, you're going to need **2 files: (1) an executable solution file** (`.m`, `.py`, or `.ipynb` file) that when run, defines the variables that will be used as solutions, and **(2) a corresponding rubric file** as a `.json` file.

**TIP:** Although you can put the rubric in the same file as the solutions, I recommend that you separate the two and simply store them in the same folder. This helps keep things organized, as the rubrics tend to get somewhat cluttered.

```
hw1/
└── hw1_solutions.ipynb
└── hw1_rubric.json
```

Change directories to the folder containing your files

```shell
cd path-to-hw1
```

and run gspack with the rubric option.

```shell
gspack --rubric hw1_rubric.json hw1_solutions.ipynb
```

This should cause your directory to look something more like

```
hw1/
└── hw1_solutions.ipynb
└── hw1_rubric.json
└── execution_log.txt
└── autograder.zip
```

where autograder.zip is what you feed to Gradescope.

**Solution and rubric file examples**

The gspack README already comes with some very informative examples that I encourage you to also look at, but here are a few more examples:

```json

```


## Resources for Coding

### C.1. Squishing multiple commits into one
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

### C.2. Basic Anaconda environment building
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
