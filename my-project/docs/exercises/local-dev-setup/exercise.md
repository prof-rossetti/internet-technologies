# Local Node.js Development Environment Setup

## Objectives

This document helps you install and configure the tools you'll need to develop Node.js (i.e. server-side JavaScript) applications on your local machine.

## Prerequisites

You should already have:

  + GitHub Account
  + GitHub Desktop software installed locally
  + Text Editor (e.g. VS Code) installed locally

## Command-line Application

The goal is to have access to a command-line application of choice, which we'll use for a variety of purposes.

Mac users who don't already have a preferred command-line application are encouraged to use the built-in Terminal application (no need to download anything, although you may want to [customize](https://github.com/prof-rossetti/intro-to-python/blob/master/exercises/command-line-computing/mac-terminal-config.md#theme) the Terminal appearance as desired).

Windows users who don't already have a preferred command-line application are encouraged to install [Git Bash](https://git-scm.com/downloads), which will allow Windows users to write the same unix-style commands as Mac users.

After installing and configuring a command line application, complete this ["Command-line Computing" Exercise](/exercises/command-line-computing/exercise.md), which will introduce you to the most useful commands.




## Node.js

The goal is to have a tool capable of running JavaScript programs on your computer.

Follow the steps in the [Node.js Overview](/notes/javascript/node.md) to install Node.js and NPM, either from the official website (recommended for beginners), or using a version manager like NVM or NVM-Windows (recommended for professionals).


After installing, you should be able to run `node --version` and see something like "v12.18.3" (or later / higher). 



## Git CLI

> NOTE: feel free to skip this section for now, unless you are running into errors saying Git needs to be installed. Later, if/when we use another tool that requires the Git CLI, we can revisit this.


Windows users who have installed Git Bash (see "Command-line Application" section above) will have satisfied the Git CLI installation requirement.

Mac users may find that Git is already installed, otherwise you are encouraged to install Git via Homebrew. See the professor's [Git installation reference](https://github.com/prof-rossetti/intro-to-python/blob/master/notes/clis/git.md#installation) for more details.

After installing the Git CLI, all students should generate SSH keys and configure their account credentials. See [Connecting to GitHub with SSH](https://docs.github.com/en/github/authenticating-to-github/connecting-to-github-with-ssh)  for more details.

If successful, you should be able to run the following command:

```sh
git --version
```



