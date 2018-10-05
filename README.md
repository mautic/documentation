# Mautic Documentation

## Introduction
This repository contains the primary [Mautic documentation][mautic-docs], the open source marketing automation system. Just as the code is open source and available for everyone, so is the documentation. Everyone is welcome to help make this information better and improve as needed.

### Download documentation as a PDF

Download the official Mautic documentation as a PDF in:
* [English][docs-eng]
* [French][docs-fr]
* [Japanese][docs-jp]


## Contributing to the Mautic documentation

This repository serves as the source code for the Mautic documentation [Gitbook][gitbook] published at [www.mautic.org/docs][mautic-docs]. The source code is shared [here on GitHub][mautic-docs-github] so anyone can contribute to the documentation in the same way the programmers do with the actual Mautic code.

### Steps to contribute

1. Fork this repository
2. Select a file to edit on your fork
3. Make your commits
4. Open a pull request to `base fork: mautic/documentation` with `base: master`
5. Include and reference any [Issues][doc-issues] your Pull Request addresses


#### Why is git used for the documentation

- *versions*. Anyone can go back and look at what the text looked like.
- *authorship*. Not only every file, but every line has its author.
- *community contributions*. No need to worry about deleting someone else's work while working on the same document.

Although some git knowledge is required to clone, modify, commit and push changes, there is a way to avoid that and edit the files directly in the GitHub web interface. If you know git, use the workflow you like. If not, the following guide will show you how to contribute easily.

### Editing documentation using the command line

1. Fork this repository
2. In the command line `cd` to where you want the documentation repository located
3. Run `$ git clone https://github.com/<your-username>/documentation.git` to clone your fork
4. Once cloning has completed, open the project in your editor of choice
5. `$ git checkout -b branch/your-branch-name` to create a new branch for your edits. Please name your branch something descriptive like `{yourusername}-revision-readme-file`
6. Commit your changes and submit your pull request to `base fork: mautic/documentation` and `base: master`

### Editing documents in the GitHub browser interface
**If you're unfamiliar with the command line but still want to contribute to the Mautic documentation**

Using *README.md* as an example:
1. [Fork][mautic-docs-fork] this repository under your account so you'll have permission to edit.
2. Select the *README.md* file (refer to the [file structure section](#file-structure) below if needed)
3. With the content of *README.md* visible, click on the pencil icon to begin editing the file
4. The *.md* extension means this file was written in Markdown, a simple but flexible text formatting language. Mautic documentation is written with [Markdown markup][markup] specifically.
5. After you've made a change, scroll down to the *Commit changes* form. Saving your change requires describing what was changed and why.
6. Before submitting your commit, select the box for *Creates a new branch* to start a new branch for your change. Name your branch something like `{yourusername}-revision-readme-file`
7. Select *Propose file change*
8. In the next dialogue box, describe what you've changed and why then select *Create pull request* to open a pull request proposing we add your changes to our official repository.

If you want to clean up after the testing, go to the *Branches* section and delete the testing branch.

<h4 id="file-structure">The File Structure</h4>

We've worked with the *README.md* file in the previous section. This file is shown in the home page of a GitHub repository and you are reading its content right now. It doesn't have anything to do with the Mautic documentation.

The *SUMMARY.md* file defines the menu of the documentation. If you add a new page to the documentation, you'll have to also add a new line there defining the title and the link to the file. It's pretty straightforward when you see the current menu items.

The folders are here to group the topics together. Open for example the *asset* folder. You'll see it has its own *README.md* file. It is the main content when you click on the Asset menu item. The *manage_assets.md* file is a subitem. The *media* subfolder contains all the images used in the *md* files.

#### Links

Often you'll want to make a link to another place in the documentation. In Markdown, the link looks like this:

```
[link title](http://example.com)
```

This will create an external link with absolute URL. If you want to create an internal link, use a relative URL like this:

```
[these steps](./../plugins/integration_test.html)
```
This will link to `plugins/integration_test.html` on the documentation website created from the *md* source file.

#### Images

As noted above, the images can be placed in the media subfolders. The images probably aren't possible to upload via the GitHub web interface, but you can upload them to any public URL and link them from there.

```
![alternative text here](http://example.com/images/apple.png "Tooltip text here")
```
Or, if you want to display an image already uploaded to the documentation repository, you can use a relative path:

```
![alternative text here](/assets/media/assets-newcategory.png "Tooltip text here")
```





<!--
Links below
-->

[mautic-docs]: https://mautic.org/docs/

[docs-eng]: https://mautic.org/docs/mautic_docs_en.pdf

[docs-fr]: https://mautic.org/docs/mautic_docs_fr.pdf

[docs-jp]: https://mautic.org/docs/mautic_docs_jp.pdf

[gitbook]: https://www.gitbook.com/

[mautic-docs-github]: https://github.com/mautic/documentation

[doc-issues]: https://github.com/mautic/documentation/issues

[mautic-docs-fork]: https://github.com/mautic/documentation#fork-destination-box

[markup]: https://daringfireball.net/projects/markdown/
