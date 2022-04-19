# The `dotenv` Package

The `dotenv` package allows a program to reference [Environment Variables](/notes/environment-variables.md) from a special file called ".env" in the root directory of the given project, instead of passing them from the command-line.

This file-based approach makes environment variables much easier to manage, especially for Windows users.

Reference: https://github.com/motdotla/dotenv.

## Installation

Installing the package:

```sh
npm install dotenv
```

## Usage


To setup this example, create a new directory on your Desktop named "my-secure-project". Then navigate there from the command-line:

```sh
cd Desktop/my-secure-project/
```

Run `npm init` to create a "package.json" file. Run `npm install dotenv --save` to install the dotenv package.

Next, create two files in the "my-secure-project" directory named ".env" and "my_script.js", respectively, and place inside the following contents:

```sh
# my-secure-project/.env

# these are environment variables:
SECRET_MESSAGE="Hello World"
MY_API_KEY="abc123"
```

```js
// my-secure-project/my_script.js

// imports a locally-installed node module called "dotenv"
const dotenv = require("dotenv")

// reads environment variables from the ".env" file and stores them in `process.env`
dotenv.config()

// accesses the named environment variables via process.env:
console.log("SECRET MESSAGE:", process.env.SECRET_MESSAGE)
console.log("API KEY:", process.env.MY_API_KEY)
```

And run the script to see the output:

```sh
node my_script.js
```

The lesson is that the `require("dotenv").config()` snippet will load environment variables from the ".env" file into the  script's environment so they can be accessed by name via the `process.env` object.

### Ignoring ".env" Files from Version Control

> SECURITY NOTE: Because these ".env" files often contain sensitive information like secret passwords and API Keys, we should absolutely avoid checking them into version control! To do this, we'll use a special ".gitignore" file.

Finally, create another file in the "my-secure-project" directory named ".gitignore", and place inside the following contents:

```sh
# my-secure-project/.gitignore

# ignore the ".env" file:
.env

```

Great! Now all subsequent commits will ignore the ".env" file from your project's version history, so you can push your code to GitHub without divulging your secret credentials.

> NOTE: if your repository already contained a ".env" file before you added the corresponding entry to the ".gitignore" file, you'll need to commit the ".gitignore" file then delete / move the ".env" file and make another commit, and then afterwards you can feel free to restore your ".env" file and it will be ignored
