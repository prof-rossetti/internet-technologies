# Express App Exercise Part 1: App Generation

## Repository Setup

First create a new repository on GitHub and call it something like "my-express-app". Include a README file and a ".gitignore" file (choosing "Node" from the dropdown).

Use GitHub Desktop to "clone" or download the repo onto your local computer, for example onto the Desktop. Navigate there from the command-line:

```sh
cd ~/Desktop/my-express-app
```


## Generating a New App


After [installing the Express Generator globally](/notes/javascript/packages/express.md#express-generator), use it to generate a new Express application in the current directory:

```` sh
express --view=ejs
````


> NOTE: by passing the `--view=ejs` option, we're specify our preference to use EJS as the "view template engine". We'll look at the EJS views later.

If it prompts you about "destination is not empty, continue? [y/N]", type y and press enter to proceed.


This should create some new files in the repository:

    bin/www
    public/javascripts
    public/images
    public/stylesheets
    public/stylesheets/style.css
    routes/index.js
    routes/users.js
    views/index.ejs
    views/error.ejs
    app.js
    package.json

Don't worry if you're unfamiliar with the location and purpose of each of these files. We will examine each at the appropriate time.

Do take a moment to observe presence of the "package.json" file, which indicates this project is an NPM project. The project's root directory doesn't contain an "index.js" file, but which file do you think is the main entry-point into this NPM project?

## Installing Dependencies

Follow the prompt to install package dependencies:

```` sh
npm install
````

## Running a Local Web Server

Run the default development web server:

```` sh
npm start

# or...
# npm run start
````

You should now be able to visit the application's home page in your browser at `localhost:3000`. Go check it out.

After demonstrating your ability to view the application locally in a browser, stop the web server with `ctrl + c`.

Nice job. Take a moment to make a new commit with a message of "Generate app".

We would otherwise be done with the setup, but before we go any further, let's take a moment to install a different web server.

## Upgrading the Local Web Server

One shortcoming of the default web server is that it requires us to restart the server each time we make a change to one of our application's files. During development, this happens a lot, so we'll want to use a different web server called [Nodemon](https://nodemon.io/), which will automatically detect file changes and obviate our need to take manual action.

Install Nodemon globally:

```` sh
npm install nodemon -g
````

In the "scripts" section of the "package.json" file, add a new "start-dev" script to invoke `nodemon` instead of `node`:

```` js
// package.json
// ...
  "scripts": {
    "start": "node ./bin/www",
    "start-dev": "nodemon ./bin/www"
  },
// ...
````

Take this opportunity to take a quick look at the `bin/www` file. Observe the code in this file defines a web server which runs on port 3000 the application logic defined by the "app.js" file.

Restart the web server:

```` sh
npm run start-dev
````

Congratulations. You've just created a new web application and viewed it locally in a browser. The next step will be to setup the application's navigational structure. Before moving on, let's make another commit with a message like "Upgrade local web server".
