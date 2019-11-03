# Contributing to the Mautic documentation

This repository serves as the source code for the Mautic documentation [Gitbook][gitbook] published at [www.mautic.org/docs][mautic-docs].
The source code is shared [here on GitHub][mautic-docs-github] so anyone can contribute to the documentation in the same way the programmers do with the actual [Mautic][mautic] code.

<!-- ## Table of Contents -->

<!--
Use this site to generate the TOC list elements:

- https://ecotrust-canada.github.io/markdown-toc/

remove the first two lines
-->

- [Why `git`](#why-git)
- [How to contribute](#how-to-contribute)
  - [Editing documentation using the command line](#editing-documentation-using-the-command-line)
  - [Editing documents in the GitHub browser interface](#editing-documents-in-the-github-browser-interface)
- [File Structure](#file-structure)
- [Style Guide](#style-guide)
  - [Whitespace and spaces](#whitespace-and-spaces)
  - [Code blocks](#code-blocks)
  - [Lists](#lists)
- [Example domain references](#example-domain-references)
  - [Standard Mautic URL example](#standard-mautic-url-example)
  - [Mautic as subdomain URL example](#mautic-as-subdomain-url-example)
  - [Mautic as subdirectory URL example](#mautic-as-subdirectory-url-example)
  - [http vs https URL example](#http-vs-https-url-example)
  - [Links](#links)
    - [Absolute links](#absolute-links)
    - [Relative links](#relative-links)
    - [Heading anchors](#heading-anchors)
  - [Images](#images)
    - [relative image links](#relative-image-links)
    - [absolute image links](#absolute-image-links)
      - [internal absolute image link](#internal-absolute-image-link)
- [Linking to Release versions](#linking-to-release-versions)

## Why `git`

Why is `git` used for the documentation

- *versions* - anyone can go back and look at what the text looked like.
- *authorship* - not only every file, but every line has its author.
- *community contributions* - no need to worry about deleting someone else's work while working on the same document.

Although some `git` knowledge is required to clone, modify, commit and push changes, there is a way to avoid that and edit the files directly in the GitHub web interface. If you know `git`, use the workflow you like. If not, the following guide will show you how to contribute easily.

## How to contribute

1. Fork this repository at [GitHub][mautic-docs-github]
1. Select a file to edit on your fork
1. Make your commits
1. Open a pull request to `base fork: mautic/documentation` with `base: master`
1. Include and reference any [Issues][doc-issues] your Pull Request addresses

### Editing documentation using the command line

1. In the command line `cd` to where you want the documentation repository located
1. Clone this repository

````console
git clone https://github.com/mautic/documentation.git --origin upstream
````

1. Fork this repository at [GitHub][mautic-docs-github] or use the [`hub`][hub] utility

````console
hub fork --remote-name origin
````

1. Once cloning has completed, open the project in your editor of choice
1. Create a new branch for your edits. Please name your branch something descriptive like `{yourusername}-revision-readme-file`

````console
git checkout -b {yourusername}-revision-readme-file upstream/master
````

1. Make your changes
1. Stage and commit your changes to your _local_ repository

````console
git status --short
git add <new and modified files>
git commit --message 'move contributing to new file'
````

1. Push to `origin`

````console
git push origin
````

1. Review the changes at your fork `https://github.com/{yourusername}/mautic-documentation`
1. Submit your pull request
    1. Direct link: `https://github.com/{yourusername}/mautic-documentation/pull/new/{yourusername}-revision-readme-file`
    1. GitHub web interface - `base fork: mautic/documentation` and `base: master` at [GitHub][mautic-docs-github]
    1. use the [`hub`][hub] utility

    ````console
    hub pull-request
    ````

### Editing documents in the GitHub browser interface

> **Note**\
> **If you're unfamiliar with the command line but still want to contribute to the Mautic documentation**

Using *README.md* as an example:

1. [Fork][mautic-docs-fork] this repository under your account so you'll have permission to edit.
1. Select the *README.md* file (refer to the [file structure section](#file-structure) below if needed)
1. With the content of *README.md* visible, click on the pencil icon to begin editing the file
1. The *.md* extension means this file was written in Markdown, a simple but flexible text formatting language. Mautic documentation is written with [Markdown markup][markup] specifically.
1. After you've made a change, scroll down to the *Commit changes* form. Saving your change requires describing what was changed and why.
1. Before submitting your commit, select the box for *Creates a new branch* to start a new branch for your change. Name your branch something like `{yourusername}-revision-readme-file`
1. Select *Propose file change*
1. In the next dialogue box, describe what you've changed and why then select *Create pull request* to open a pull request proposing we add your changes to our official repository.

## File Structure

The **`README.md`** file serves as the introduction and description of this repository. This file does not contain any product documentation.

The **`SUMMARY.md`** file defines the menu of the documentation. If you add a new page to the documentation, you'll have to also add a new line there defining the title and the link to the file (formatted like the existing menu items).

The folders in this repository are grouped together by topic. For example, within the *asset* folder, you'll see it has its own **`README.md`** file (becomes `./index.html`) which contains the primary description of the Asset menu; the *manage_assets.md* file is a subitem; the *media* subfolder contains all the images used in the *.md* files.

## Style Guide

The style guide section is very much a :construction: Work in Progress.

Please contribute :)

### Whitespace and spaces

- One blank line around headings
- One blank line around list items
- One blank line around code blocks
- One final blank line

- Two spaces after a full stop.  Next sentence.

### Code blocks

- prefer fenced codeblocks with three backticks
- must have [language identifier][linguistic]
  - use `text` if not special 

### Lists

* Use `1.` only for numbered lists.
* use `*` for unnumbered lists
* indent 4 spaces for a second level

<details><summary>markdown</summary>

```markdown
1. Item the first
1. Something else
   1. indent 4 spaces
   1. for a second level
1. And finally
   * minor point
* not a number
```

</details>

<details><summary>result</summary>

1. Item the first
1. Something else
   1. indent 4 spaces
   1. for a second level
1. And finally
   * minor point
* not a number

</details>

## Example domain references

Please use `example.com` as the reference domain for documentation.

### Standard Mautic URL example

    https://example.com

### Mautic as subdomain URL example

    https://mautic.example.com

### Mautic as subdirectory URL example

    https://example.com/mautic

### http vs https URL example

Use the `https://` protocol in documentation.  We want to promote good practices.

    https://example.com

If you need to show both protocols, add brackets around the `(s)`

    http(s)://example.com

### Links

Often you'll want to make a link to another place in the documentation.  We prefer to group links at the bottom of a page, and provide a reference macro in the text.
This make linking to the same place much easier.  In Markdown, it looks like this:

#### Absolute links

```markdown
Aut et laudantium ad [ratione id][link macro]. Ut similique quis et ut. Consectetur eum quia totam [recusandae][link macro] necessitatibus dolorem debitis.

[link macro]: <http://example.com>
```

#### Relative links

These will link to `plugins/integration_test.html` on the documentation website created from the *`plugins/integration_test.md`* source file.

```markdown
[integration test]: <integration_test.html>
[integration test]: <./../plugins/integration_test.html>
```

#### Heading anchors

Heading anchors enable linking directly to a Markdown heading from within the same document very easily.  The anchors are auto-generated for all headings.
The link target is specified inline.

```markdown
Aut et laudantium ad [ratione id](#heading-anchors). Ut similique quis et ut. Consectetur eum quia totam [recusandae](#style-guide) necessitatibus dolorem debitis.
```

### Images

Images should be placed in the media subfolders in the different sections of this repository.

Link format:

```markdown
![alternative text here](image-reference.png "Tooltip text here")
```

#### relative image links

To display an image already in the documentation repository, use a relative path.

```markdown
![form rebuild cache](media/rebuild.png "Rebuild form cache"")
![form rebuild cache](./../forms/media/rebuild.png "Rebuild form cache")
```

#### absolute image links

For images that cannot be uploaded via the GitHub web interface, upload them to a public URL service and use the generated link.

```markdown
![apple](http://example.com/images/apple.png "Like this delicious apple")
```

##### internal absolute image link

> **Warning**\
> This link format should not be used.

```markdown
![form rebuild cache](/forms/media/rebuild.png "Rebuild form cache")
```

## Linking to Release versions

Use an [absolute external link](#absolute-links) to reference the official released versions of Mautic.  Include `Mautic` and the version number in the link macro.
All version numbers have 3 components: `<major>.<minor>.<patch>`

```markdown
Since [Mautic 2.9][release-2.9.0], when...

[release-2.9.0]: <https://github.com/mautic/mautic/releases/tag/2.9.0>
```

<!-- markdown style links -->

[mautic-docs]: <https://mautic.org/docs/>
[mautic-docs-github]: <https://github.com/mautic/documentation>
[mautic-docs-fork]: <https://github.com/mautic/documentation#fork-destination-box>
[doc-issues]: <https://github.com/mautic/documentation/issues>

[mautic]: <https://github.com/mautic/mautic>

[gitbook]: <https://www.gitbook.com/>

[hub]: <https://github.com/github/hub/releases>
[linguistic]: <https://github.com/github/hub/releases>