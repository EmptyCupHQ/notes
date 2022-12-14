# MkDocs

[Mkdocs](https://www.mkdocs.org/) is a static site generator that is mainly used for documentation.

mkdocs "builds" (or generates) HTML documentation from content files written in [Markdown](/basics/markdown.md). It comes with a built in development server to preview the documentation locally and a feature to deploy a live version to [Github Pages](/basics/gh-pages.md).

It can be configured using a single YAML file `mkdocs.yml` present in the root directory.


### Requirements

Python (as MkDocs is a Python package)

- To check if python is installed on your system run `python --version` in the command line.
- If the output is something like `Python 3.10.6` then you have python installed, skip to pip.
- If the output is something like `Command 'python' not found,...` then run `sudo apt-get install python3` and follow the commands to get python installed in your system.

pip (most common python package manager)

- To check if you already have pip installed run `pip --version` in the command line.
- If the output is something like `pip 22.0.2 from /usr/lib/python3/dist-packages/pip (python 3.10)` then you have pip installed, skip to MkDocs installation.
- If the output is something like `Command 'pip' not found,...` then first run `sudo apt update` then run `sudo apt install python3-pip`, confirm for the pip installation.

!!! warning ""
    TODO: Installing python & pip should be moved into a separate note as it may be referred by multiple sources. DRY.

!!! warning ""
    TODO: Add instructions to setup a virtualenv to maintain a clean environment

### Installation
  - To install mkdocs run `pip install mkdocs`, to confirm the installation run `mkdocs --version`.
  - Then you require to install material (theme of mkdocs used in the project) using `pip install mkdocs-material`
  - run `mkdocs serve` in the project directory to start a local development server. If you are able to see the project deployed then installation was successful.


### Workflow

In the project folder there is a `docs` folder which contains all the markdown files used to build the documentation, by convention `docs/index.md` is the homepage. You can add content by editing the files or adding a new file.

Below is step by step workflow for adding & publishing a new note:

1. Add a note:
    - First check under which directory in `docs` you need to add the file, you can do so by checking the note's place in the site tree, which is mentioned in the `nav:` in the `mkdocs.yml` file.
    - Add and edit `note_name.md` in the proper directory and save it.
2. Preview the note:
    - run `mkdocs serve` it starts a local development server to see how the site will look published.
    - after every edit just save your edits locally and the page auto-updates itself.
3. Publish to GitHub Pages:
    - once you are done making edits on the project you can publish the project on github pages, run `mkdocs gh-deploy` to do so.
    - this will build the docs and commit them to gh-pages branch and push the gh-pages branch to GitHub and documentation should appear at `<username>.github.io/<repository>`.


!!! note ""
    `mkdocs serve` doesn't generate the build folder. It directly serves from the markdown files. The build folder `site` can be generated by using `mkdocs build`, if necessary.

    `mkdocs gh-deploy` builds the documentation and adds all the build output files to a separate `gh-pages` branch and commits and pushes to GitHub triggering a publish.


### mkdocs.yml

A quick reference for key settings:

- `site_name` is displayed on the top left of the documentation site.
- `theme` sets the theme name and theme specific configuration. Learn more.
- `nav` defines the structure of the sidebar in the " - Title: ./file/path" format.