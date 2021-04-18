# Server-side JavaScript Exercise

Use NPM to create a new Node.js project, install a third-party open source JavaScript library, and execute a script which utilizes that library.

## Objectives

  1. Run server-side JavaScript applications with Node.js.

## Prerequisites

  + [Command-line Computing Exercise](https://github.com/prof-rossetti/intro-to-python/blob/master/exercises/command-line-computing/README.md)
  + [Node.js Overview](/notes/javascript/node.md)
  + [Node Package Management (NPM) Overview](/notes/javascript/npm.md)

## Instructions

After installing Node.js and NPM via the prerequisite instructions, we should be able to use it to create and run applications.

### Initializing Projects

Create a new directory on the Desktop called something like "my_node_project", and navigate there from the command-line.

From the project directory, initialize a new Node.js project:

```sh
npm init
```

This process will ask you to specify the name of your project and some other metadata. You can leave most of the fields blank or use defaults by pressing "enter". Make sure to choose "index.js" as the entry point.

When complete, this process will create a new file in the project directory called "package.json", which contains metadata about the project, the names and versions of all the project's dependencies, and the commands used to test and run it.

### Creating Programs

During the project initialization, we specified an "entry point" or chose the default entry point of "index.js". This is somewhat analogous to the "index.html" file being the entry point of a website project.

Create a new file in the project directory called "index.js", and place inside the following contents:

```` js
// this is the "index.js" file...
console.log("RUNNING RUNNING RUNNING")
````

### Running Programs

We can use either the `node` utility or the `npm` utility to run the program.

When using `node` to run the program, we specify the program's filepath:

```` js
node index.js
````

We can also optionally register a short-cut / alias for this command in the "scripts" section of the project's "package.json" file. For example, see the "go-go-go" alias below:

```` js
{
  "name": "my_node_project",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "go-go-go": "node index.js"
  },
  "author": "",
  "license": "ISC"
}
````

If specifying the alias in this way, we can use `npm run` to run it:

```` js
npm run go-go-go
````

Nice, you now know how to create and run Node.js apps.

### Managing Dependencies

Let's practice running a script which will require us to use some package dependencies, like some array methods from the "d3" package. Create a new file in the project directory called "calculate.js" and place inside the following contents:

```js
// this is the "calculate.js" file...

var d3 = require("d3") // assign the locally-installed D3 module to a variable called d3 for further invocation. You can choose any variable name you want, but why not choose the official name we're already familiar with?

var someIntegers = [9, 13, 99, 3]
console.log("THE ARRAY IS:", someIntegers)

var maxNumber = d3.max(someIntegers)
console.log("MAXIMUM NUMBER IN THE ARRAY IS:", maxNumber)
```

Since this program requires the "d3" module, let's install that now for the first time:

```sh
npm install d3 --save
```

Notice when we run the `npm install` command for the first time, it generates a new directory called "node_modules" and installs the specified package(s) inside. When we run this command with the `--save` flag, it also adds the package name to the "dependencies" section of the "package.json" file, and uses a file called "package-lock.json" to track more metadata about the package versions.

> FYI: If our project is a Git repository, we'll want to include a `node_modules` entry in the project's ".gitignore" file, to ignore the "node_modules" directory from version control.

Finally, demonstrate your ability to run this new program:

```sh
node calculate.js
```

Nice, you now know how to install and use third-party Node.js modules!
