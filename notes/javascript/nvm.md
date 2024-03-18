# Node Version Manager (NVM)

Instead of installing a specific version of Node.js from their website, we'll use the Node Version Manager (NVM) for a more professional experience. NVM is a version manager that will allow us to install any version of Node.js, and switch between versions as necessary. This is especially helpful when we work on different projects that require different versions. 

## Installation

To install NVM, use one of the links below, depending on your computer's operating system:

  + [`nvm` (Mac OS)](https://github.com/creationix/nvm)
  + [`nvm-windows` (Windows OS)](https://github.com/coreybutler/nvm-windows#installation--upgrades)

Once you have installed NVM, you can use it to download Node.js by following the "Usage" section below.

## Usage

List available versions of Node.js:

```sh
nvm list available
```

Download a specific version (choose a version number based on the previous output):

```sh
nvm install 21.71.
```

Activate / use the specific version you downloaded.

```sh
nvm use 21.71.
```

Now you should have access to run `npm` and `node` commands within the context of your project. See the [NPM Overview](/notes/javascript/npm.md) for more details.
