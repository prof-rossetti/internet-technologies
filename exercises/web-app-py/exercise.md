# "Web Application" Exercise

## Reference Material

  + [The `flask` Python Package](https://flask.palletsprojects.com/en/1.1.x/)
  + [Example Flask Applications](https://github.com/prof-rossetti/intro-to-python/blob/master/notes/python/packages/flask.md#usage)

## Objectives

  + Gain familiarity with server-side software like web applications.
  + Practice your ability to run existing web applications.
  + Observe the web application's source code to identify patterns, and try to adapt the code to suit your purposes.

## Instructions

In this exercise, we'll demonstrate our ability to run existing web applications built in Python.

### Basic Web App

We'll be starting with this basic [Rock-Paper-Scissors web app](https://github.com/prof-rossetti/rock-paper-scissors-flask). Visit the repository on GitHub, and follow the instructions in the README file to download and setup this application, and run it locally.

Once you've demonstrated your ability to run the application locally in your web browser, observe the source code and try to identify patterns. Observe how the applications "routes" control what will happen when a certain URL path is visited. Observe how the "view templates" (or individual web pages) inherit from a shared layout, which eliminates duplicate front-end HTML code.

### Database-backed Web App

Many web applications facilitate the storage and retrieval of information from a database. Relational databases and SQL are outside the scope of this course, so we'll be using a Google Sheet as our database.

Reference this example [Products web app](https://github.com/prof-rossetti/web-app-starter-flask-sheets). Visit the repository on GitHub, and follow the instructions in the README file to 1) download the repo onto your local computer, 2) set up Google Sheets API credentials, and 3) run the app locally.
