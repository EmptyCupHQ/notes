# Getting Started

This repository of notes is intended for quick reference, especially for beginners.
This is not a textbook. Focus of each note is to provide minimal, dense, clutterfree info for the reader  to get started.

## Step 1: Setting up

1. First you need to have a clean linux operating system setup. You can install Ubuntu 20.04 on VirtualBox or VMWare workstation if you have a laptop with 4-8GB RAM.
2. Install Visual Studio Code or any other code editor you prefer.
3. Install Git on your laptop. Sign up for an account on Github. [Then setup SSH access.](/basics/git-ssh)


## Step 2: Working locally

1. Fork the [original repository](https://github.com/emptycuphq/notes) to your own account.
2. Clone your forked repository to your laptop.
3. [Install python-virtualenv and setup a virtualenv with name 'venv' in the code folder.](/basics/python-venv/)
4. [Activate the virtualenv and install the pip dependencies](/basics/python-pip/).
5. Start the local development server with: `mkdocs serve`


## Step 3: Submit a pull request

1. Open the folder in the editor. [Understand how material for mkdocs works.](basics/mkdocs)
2. Make edits in the `docs` folder to edit the contents.
3. Navigate to your [local deployment](http://127.0.0.1:8000/notes/) to test the changes.
4. Keep making changes till you are satisfied. Then [commit the changes](/basics/git-basics).
5. Push to your github account with `git push`.
6. Navigate to the forked repository in your github account using your browser and submit a pull request to the original repository.
7. [Raise a github issue on the original repository](https://github.com/EmptyCupHQ/notes/issues), if you face any issues.
