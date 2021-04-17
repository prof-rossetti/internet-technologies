# Server-side JavaScript Exercise

Use NPM to create a new Node.js project, install a third-party open source JavaScript library, and execute a script which utilizes that library.

## Objectives

  1. Run server-side JavaScript applications with Node.js.

## Prerequisites

  + Command-line Computing Exercise
  + [Node.js Overview](/notes/javascript/node.md)
  + [Node Package Management (NPM) Overview](/notes/javascript/npm.md)

## Instructions

After installing Node.js and NPM via the prerequisite instructions, we should be able to use it to run existing applications, and create new applications.

### Running Existing Applications

Fork the professor's [Example Node.js App](_________) repo. The clone or download the repo onto your local machine. Open the repo in your text editor, and navigate to the repo from the command-line. Follow the instructions in the repo's README.md file to run it.

### Creating New Applications

#### Initializing a Node.js Project

Create a new directory on the Desktop called something like "my_node_project", and navigate there from the command-line.

From the project directory, initialize a new Node.js project:

```sh
npm init
```

This process will ask you to specify the name of your project and some other metadata. You can leave most of the fields blank or use defaults by pressing "enter". Make sure to choose "index.js" as the entry point.

When complete, this process will create a new file in the project directory called "package.json", which contains metadata about the project, the names and versions of all the project's dependencies, and the commands used to test and run it.

### Creating a New Program

During the project initialization, we specified an "entry point" or chose the default entry point of "index.js". This is somewhat analogous to the "index.html" file being the entry point of a website project.

Create a new file in the project directory called "index.js", and place inside the following contents:

```` js
// this is the "index.js" file...
console.log("RUNNING RUNNING RUNNING")
````

### Running the Program

We can use either the `node` utility or the `npm` utility to run the program.

#### Running via Node.js

When using `node` to run the program, we specify the program's filepath:

```` js
node index.js
````

#### Running via NPM

We can alternatively register a short-cut or alias for this command in the "scripts" section of the project's "package.json" file. For example, see the "go-go-go" alias below:

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

When using `npm` to run the program, we specify its alias:

```` js
npm run go-go-go
````

### Extending the Project

Let's practice running a script which will require us to use some package dependencies, like some array methods from the "d3" package.


Create a new file called "calculate.js" and place the following contents inside:

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

To ignore the "node_modules" directory from version control, let's create a new file in the project directory called ".gitignore" and place the following contents inside:

```sh
# this is the .gitignore file
node_modules
```

Finally, demonstrate your ability to run this new program:

```sh
node calculate.js
```
