---
title: Creating a New Package
summary: Creating a Package For Inclusion in the Repositories
sidebar_position: 3
---

# Creating a New Package

This page will take you through the steps required to build a new package for the Solus package repositories. For this example, we will use the command line utility [tree](https://gitlab.com/OldManProgrammer/unix-tree), which is already packaged for Solus, but we will pretend like it's not.

:::note

**Please [look to see if an issue has been filed](https://github.com/getsolus/packages/issues?q=sort%3Aupdated-desc+is%3Aopen+label%3A%22Package%3A+Addition+Request%22) and _accepted_ for the software or library you intend to package**. If there is an existing request, please add a link to it in your pull request. Ex:

```
This PR resolves software request https://github.com/getsolus/packages/issues/123
```

:::

### Update an existing clone

If you do not have a local clone set up yet, see [Prepare for Packaging](prepare-for-packaging.md#fork-the-getsoluspackages-repository)

Bring your local clone up to date. Run:

```bash
cd ~/solus-packages
git switch main
git pull
```

## Create a new branch

It's always a good idea to switch to a new git branch before beginning packaging work. This helps to separate your work from any new changes made to the package repository, which will allow you to more easily rebase any changes if needed. To do so run:

```bash
git switch -c your-branch
```

## Create the `MAINTAINERS.md` file

You must add a file called `MAINTAINERS.md` using the template in [Maintainership](procedures/maintainership.md). Solus uses this to track the primary maintainer(s) for each package.

## Create the `package.yml` file

You will need a link to the most recent source tarball for this from the software's website.

To create a skeleton `package.yml` file, use the `go-task new` command.

This command takes two arguments, in the following order:

1. Package name
2. Source URL

```bash
go-task new -- tree https://gitlab.com/OldManProgrammer/unix-tree/-/archive/2.1.1/unix-tree-2.1.1.tar.gz
```

The `go-task new` command will automatically place the new `package.yml` in the proper directory according the package name, _and will overwrite any existing `package.yml` file at that location_.

:::note
You can, of course, create your `package.yml` file entirely from scratch, but `go-task new` will give you a better starting point. We recommend using the `go-task new` command.
:::

Now you should have a `package.yml` file that looks something like this:

<!-- prettier-ignore -->
```yaml
name       : unix-tree
version    : 2.1.1
release    : 1
source     :
    - https://gitlab.com/OldManProgrammer/unix-tree/-/archive/2.1.1/unix-tree-2.1.1.tar.gz : bcd2a0327ad40592a9c43e09a4d2ef834e6f17aa9a59012a5fb1007950b5eced
homepage   : PLEASE FILL ME IN
license    : GPL-2.0-or-later # CHECK ME
component  : PLEASE FILL ME IN
summary    : PLEASE FILL ME IN
description: |
    PLEASE FILL ME IN
builddeps  :
setup      : |
    %configure
build      : |
    %make
install    : |
    %make_install
```

The `go-task new` command has filled many fields for us, but not all of them will be right, and some of them need to be filled in. Refer to the [package.yml page](docs/packaging/package.yml.md) to see how each field should be used.

For this example, we need to fix the following:

- The name needs to be `tree`, so update it.
- The `license` is correct, so we remove the comment. License values need to match an "Identifier" in the [SPDX License List](https://spdx.org/licenses/).
- Fill in `homepage`, `component`, `summary`, and `description`.
- Remove `builddeps`. This package has no build dependencies beyond the ones already available for every package (the `system.devel` packages).
- The `setup` step is not required, remove it.
- In the `install` key, we can't use the `%make_install` macro for this package. The files are installed in their correct locations individually.

After updating the file, it will now look like:

<!-- prettier-ignore -->
```yaml
name       : tree
version    : 2.1.1
release    : 1
source     :
    - https://gitlab.com/OldManProgrammer/unix-tree/-/archive/2.1.1/unix-tree-2.1.1.tar.gz : bcd2a0327ad40592a9c43e09a4d2ef834e6f17aa9a59012a5fb1007950b5eced
homepage   : https://gitlab.com/OldManProgrammer/unix-tree
license    : GPL-2.0-or-later
component  : system.utils
summary    : list contents of directories in a tree-like format.
description: |
    Tree is a recursive directory listing command that produces a depth indented listing of files, which is colorized ala dircolors if the LS_COLORS environment variable is set and output is to tty
build      : |
    %make
install    : |
    install -Dm00664 $workdir/doc/tree.1 $installdir/usr/share/man/man1/tree.1
    install -Dm00755 $workdir/tree $installdir/usr/bin/tree
```

To read more about finding and including dependencies and other parts of `package.yml` please see [Packaging Practices](packaging-practices.md).

Understanding how to translate source code into a good `package.yml` file is the heart of packaging. If you are stumped, or have questions, **ask for help in our Solus Packaging room on [Matrix](/docs/user/contributing/getting-involved#matrix-chat).**

## Build the package

Build the package using `go-task`. The default task will build the package against the Unstable repository, so you don't have to specify a task here.

```bash
go-task
```

Once the build completes, your directory should now include the following files:

```text
├── abi_used_libs
├── abi_used_symbols
├── package.yml
├── pspec_x86_64.xml
└── tree-2.1.1-1-1-x86_64.eopkg
```

All these files _except_ the `.eopkg` file(s) should be included in your pull request. You will remove the `.eopkg` files after testing the package.

Once your package has built successfully, you will need to [test it](testing-a-package).

## Commit your changes

Check the [changes in your files](git-basics#check-the-changes-in-your-files).

[Add / remove files as necessary to the commit](git-basics.md). Then, **check your branch**.

Double-check that everything looks correct and all of the files have been staged before committing.

```bash
git status
```

If all looks well, commit your changes.

```bash
git commit
```

### Commit message format for new packages

`git commit` on [an initialized repository](prepare-for-packaging.md#initialize-git-hooks-for-linting) will automatically open your editor with the correct template.
Note that lines starting with a `#` will be ignored by Git and do not need to be removed.

There should be a summary line (with the package name), a blank line, and then the rest of the commit message.

- There should at the minimum be a Summary.
- Bullet point lists should start with a dash.
- Link the package request using a `Resolves` line.

Here is an example in our standard format:

```
tree: Add at v2.1.1

**Summary**

Add the tree package, which recursively lists directories in a tree like manner.

Resolves getsolus/packages#issuenumber
```

Where `issuenumber` is the issue number of the package request.

For more information on suitable commit messages, please check the [tooling central documentation](https://github.com/solus-project/tooling-central/blob/master/README.rst#using-git).

If you need a change to depend on another change, mention it in the commit message too (use the full URL): `Depends on https://github.com/getsolus/packages/issues/234`

Next, you'll [submit a pull request for review](submitting-a-pull-request.mdx).
