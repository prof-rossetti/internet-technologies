
# The Express Package

> Express is a minimal and flexible Node.js web application framework that provides a robust set of features for web and mobile applications. - [Express website](https://expressjs.com/)

Express provides a framework for creating web applications in Node.js. Express allows us to specify response logic that should be performed by a web server when it receives requests at various URL endpoints.

## References

Source Code: https://github.com/expressjs/express.

Documentation: https://expressjs.com/en/4x/api.html.

Getting Started Guides:

  + https://expressjs.com/en/starter/installing.html
  + https://expressjs.com/en/starter/hello-world.html
  + https://expressjs.com/en/starter/generator.html
  + https://expressjs.com/en/starter/basic-routing.html
  + https://expressjs.com/en/starter/static-files.html

## Installation

If installing into a local NPM project:

```sh
npm install express --save
```

### Express Generator

Instead of creating and configuring our own Express applications from scratch, we will use the Express Generator NPM package to generate a new express application for us.

Install the Express Generator globally:

```` sh
npm install express-generator -g
````

> NOTE: passing the `-g` flag denotes a global installation. Global installations generally allow the module to be invoked from the command line, even outside of a NPM project directory.
