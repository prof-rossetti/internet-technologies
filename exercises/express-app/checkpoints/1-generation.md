# Express App Checkpoint 1: App Generation

## Generating a New App

First use the command-line to navigate to a place where you keep your programming projects (like the Desktop).

```sh
cd ~/Desktop
```

After installing the Express Generator globally, use it to generate a new Express application, for example one named "my_app", :

```` sh
express my_app --view=ejs
````

> Note: by passing the `--view=ejs` option, we're specify our preference to use EJS as the "view template engine". We'll look at the EJS views later.

This command should create a directory named "my_app/" which contains the following files:

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

Follow the prompt to navigate into the project directory and install package dependencies:

```` sh
cd my_app

npm install
````

## Running a Local Web Server

Run the default development web server:

```` sh
# Mac Terminal:
DEBUG=my_app:* npm start

# Windows Command Prompt:
set DEBUG=myapp:* & npm start
````

You should now be able to visit the application's home page in your browser at `localhost:3000`. Go check it out.

After demonstrating the ability to view the application locally in a browser, stop the web server by typing `ctrl-c`.

Nice job. We would otherwise be done with the setup, but before we go any further, let's actually install a different web server, and take a moment to setup version control.


## Configuring Version Control

Usually we download repos from GitHub, but this time our directory started locally, so our workflow is a little different to get the version control set up.

First, from the project's root directory, let's initialize a new Git repo:

```sh
git init .
```

Let's add a ".gitignore" file with the following contents inside:

```sh
# this is the ".gitignore" file...

.DS_Store
.env
node_modules
```

Let's make our first local commit:

```sh
git add .
git commit -m "Generate new express app"
```

As a one-time step, we'll create a new repo on GitHub, locate it's SSH remote address, and associate that address with our local repo:

```sh
git remote add REMOTE_SSH_ADDRESS
```

Finally, we should now be able to push our changes to GitHub:

```sh
git push origin main
```

> NOTE: if you see an error like "Updates were rejected because the tip of your current branch is behind its remote counterpart", then we'll use a forced push for the first time `git push origin main -f`.


> NOTE: if you see an error like "refspec main does not match any", we'll need to [change the name of your local default branch](https://github.com/prof-rossetti/intro-to-python/issues/78) to "main" before trying to push again.

Once you can see your code on GitHub, we can get back into the Express part of this exercise...

## Upgrading the Local Web Server

One shortcoming of the default web server is that it requires us to restart the server each time we make a change to one of our application's files. During development, this happens a lot, so we'll want to use a different web server called [Nodemon](https://nodemon.io/), which will automatically detect file changes and obviate our need to take manual action.

Install Nodemon globally:

```` sh
npm install nodemon -g
````

In the "scripts" section of the "package.json" file, modify the "start" script to invoke `nodemon` instead of `node`:

```` js
// package.json
// ...
  "scripts": {
    "start": "nodemon ./bin/www",
  },
// ...
````

Take this opportunity to take a quick look at the `bin/www` file. The code in this file defines the web server which runs on port 3000 the application logic defined in "app.js".

Restart the web server:

```` sh
# Mac Terminal:
DEBUG=my_app:* npm start

# Windows Command Prompt:
set DEBUG=myapp:* & npm start
````

Congratulations. You've just created a new web application and viewed it locally in a browser. The next step will be to setup the application's navigational structure. Before moving on, let's make another commit with a message like "Upgrade local web server".
