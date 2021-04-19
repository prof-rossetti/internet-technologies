# Node Package Manager (NPM)

In the Node.js ecosystem, third-party JavaScript libraries are called "packages" and we can install them using the [Node Package Manager (NPM)](https://www.npmjs.com/).

## Detection

NPM usually comes pre-installed when you install Node. Check to see if NPM is installed, and if so, where:

```` sh
# Mac Terminal / Windows Git Bash:
which npm

# Windows Command Prompt:
where npm
````

Checking to see which version is installed:

```sh
npm -v
```

## Installing Packages

When installing third-party packages, you have the option to install them "globally" or "locally," and the installation method differs slightly for each. Generally, the package documentation will tell you whether to install locally or globally.

### Installing Packages Globally

By installing a package "globally", you install it onto your machine in a shared place for use within any of your projects. Packages that provide command-line utilities are often installed this way.

```` sh
npm install MODULE_NAME -g
````

### Installing Packages Locally

By installing a package "locally", you install it within the "node_modules" directory of a specific project you are working on, and only files within that project will have access to the installed modules.

This is often useful if you are working on multiple projects at the same time which use different modules or different versions of the same module.

#### The "package.json" File

References:
  + https://docs.npmjs.com/files/package.json
  + https://docs.npmjs.com/files/package.json#main
  + https://docs.npmjs.com/files/package.json#scripts

To manage the module dependencies of your project, create a new file called "package.json" in that project's root directory (most commonly by running the `npm init` command in that directory). Then within the "package.json" file, specify a list of packages and their versions. From within the project's root directory, run `npm install` to install all packages listed in the "package.json" file.

Installing existing modules listed in the "package.json" file:

``` sh
npm install
```

Installing a new module locally and adding it to the "package.json" file for the first time:
```sh
npm install MODULE_NAME --save
````
