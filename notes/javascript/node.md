# Node.js Overview

Up until this point we have been using JavaScript on the "client-side" - executed and interpreted by a web browser.

[Node.js](https://nodejs.org/en/) allows us to install an interpreter onto our local machines that will allow us to run JavaScript scripts on the "server-side".

> Node.js is a JavaScript runtime built on Chrome's V8 JavaScript engine. Node.js uses an event-driven, non-blocking I/O model that makes it lightweight and efficient. Node.js' package ecosystem, npm, is the largest ecosystem of open source libraries in the world. - [Node.js website](https://nodejs.org/en/)


## References

  + [Node.js Source Code](https://github.com/nodejs/node)
  + [Node.js Documentation](https://nodejs.org/api/)

## Detection

First, check if node is installed on your computer, and if so, which version:

```` sh
# Mac Terminal:
which node

# Windows Command Prompt:
where node
#> /Users/YOUR_USERNAME/.nvm/versions/node/v6.6.0/bin/node
````

```sh
node -v
#> v6.6.0
```

## Installation

If Node isn't already installed on your computer, you need to install it. There are two general ways to do this:

  A. Install the **latest version** of Node.js from https://nodejs.org/en/download/ -- EASY WAY
  B. Install a **version manager**, and use that to install a specific version of Node.js. If installing via a version manager, choose one depending on your operating system:

  + [`nvm` (Mac OS)](https://github.com/creationix/nvm)
  + [`nvm-windows` (Windows OS)](https://github.com/coreybutler/nvm-windows#installation--upgrades)


## Usage

Once you have installed Node, you should be able to use it to run scripts. For example, if you have a file called "my_script.js" file on your Desktop with the following contents inside:

```` js
// this is a file on the Desktop called my_script.js
console.log("HEY WE ARE RUNNING JAVASCRIPT ON THE SERVER-SIDE!")
````

Run the script from anywhere:

```` sh
node ~/Desktop/my_script.js
````

> NOTE: You either need to run the script from within the directory where it exists, or invoke it with a more specific file path (e.g. `node ~/Desktop/my_script.js`).

## [NPM](npm.md)

Once you have installed Node, you also get NPM, the Node Package Manager.
