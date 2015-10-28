# Version control with git

As stated on the project's official website [git-scm.com](https://git-scm.com),

> Git is a free and open source distributed version control system designed to
> handle everything from small to very large projects with speed and
> efficiency.

Great so this means that here we have a tool that we can use free of charge
(even better, we can look at and modify the source code) which allows us to
version our projects. Versioning in turn means that we can keep a history of
changes made to the project in question. Additionally it is distributed which
for practical purposes means that me keeping a history does not depend on the
benevolence (or even existence) of some remote server. The following tutorial is
intended to

> ## Learning Objectives
>
>  1. Convince you of Git's superiority
>  2. Teach you to use Git locally to version changes on a local project
>  3. Teach you to use Git to collaborate with others on remote projects

We hope that at the end of the day (or at least after the first time Git has
saved you from losing your progress) you will accept that it is _the best and
only way_ to version anything from your diary to your future company's software.


## Motivation
Does the situation depicted in [this PhD
comic](http://www.phdcomics.com/comics/archive.php?comicid=1531) look anything
familiar to you? What the student in this comic clearly needs (apart from some
LaTeX lessons) is a version control system! Such a system keeps a history of
project in a very non-intrusive way. The user only sees the current state of the
project in their filesystem but all changes are versioned such that previous
version are easily accessible. This reduces the need for ridiculous
`_version5.23_final` filename appendices.

Another common challenges that every physics student has to face in their time
at university is collaborative work with fellow students. Let's take a lab
course for example: You gather data, analyse it, and write a report about your
findings. There's a lot to be versioned: your data (although it will not change
after it's been recorded), your analysis programs, and the LaTeX source of your
report.

 * Superiority over exchanging files via email
 * Superiority over exchanging files via Dropbox
 * Two sides: Collaboration and backup/history


## Git-ing started
Before you can use Git, you need to configure it. This is necessary, as Git
will use your name and email address to reference the changes you made to a
project. Run the following commands in your terminal substituting your name and
email address accordingly:

```bash
git config --global user.name "Name Surname"
git config --global user.email "name.surname@cern.ch"
```

You can also set other options like for example coloured output with the same
command:

```bash
git config --global color.ui auto
```

You can view all your settings by running `cat ~/.gitconfig`. You can also edit
this file by hand if you know what you're doing. Extensive documentation can be
found on the `git-config` manpage (run `man git-config`) or in the [online
documentation](https://git-scm.com/docs/git-config).
 

## Concepts


## Creating a repository


## Managing changes


## Collaborating
One important feature is the `.gitignore` file. It defines a list of files
(wildcards are possible) that should always be ignored by Git for the current
repository. For example, if you are collaborating on a paper in LaTeX, you will
want to put your `.tex` files under version control but not any of the
intermediate files produced by your LaTeX compilation. In your repository's root
folder, create a file called `.gitinore` and fill it with the following lines:

```
*.acn
*.acr
*.alg
*.aux
*.bbl
*.blg
*.dvi
*.glg
*.glo
*.gls
*.idx
*.ilg
*.ind
*.ist
*.lof
*.log
*.lot
*.maf
*.mtc
*.mtc1
*.out
*.synctex.gz
*.toc
```

Please not that this list does not include `.pdf` files as you will probably add
figures as PDF files. You will want to add your resulting `.pdf` file to that
list above to keep the (dynamic) binary file from being put under version
control.

For files that are specific to your system (like `.DS_Store` files on OS X or
`.swp` files if you are using Vim) you can globally define a list of file types
that should be ignored by Git. Those files have nothing to do with your project
and are specific to _your_ system. Your collaborator might be using Emacs on
Linux and therefore not care about those files. Create a new file in your home
directory called `.gitignore` and add the following lines:

```
.DS_Store
*.swp
```

Then run the following command

```bash
git config --global core.excludesfile $HOME/.gitignore
```

This will tell Git to ignore all files named `.DS_Store` or those files ending
in `.swp`.
