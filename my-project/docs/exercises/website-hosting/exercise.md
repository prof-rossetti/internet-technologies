# "Website Hosting" Exercise

Leverage an existing open source website to publish your own.

> NOTE: your website content will be accessible to the public.

## Objectives

  1. Practice using web development tools like a text editor, web browser, and version control software.
  1. Gain exposure to a basic website repository, including its directory structure and HTML document contents.
  3. Publish a website to the Internet.
  2. Make changes to website contents, and re-publish.

## Prerequisites

  + Sign up for a [GitHub](https://github.com/) account, unless you already have one. New users make sure to verify your email address by clicking the confirmation link sent via email.
  + Download a text editor like [VS Code](https://code.visualstudio.com/).
  + Download the [GitHub Desktop](https://desktop.github.com/) software.

## Instructions

### Copying a Repository Template

Sign in to GitHub and navigate to the professor's [Student Site](https://github.com/prof-rossetti/student-site) repository. This repository contains an "index.html" file and other HTML files which comprise a basic website.

Use this repository as a "Template" to create a copy of the repository under your own control. Navigate to your repository's homepage on GitHub, if necessary.

Great, now you have some example website code.

### Configuring Hosting

Let's configure a [GitHub Pages](https://pages.github.com/) server to host our website.

Navigate to your repository's "Settings" menu on GitHub, and scroll down to find the section called "GitHub Pages". Select the "main" branch from the drop-down, and click "Save". Visit the resulting GitHub Pages URL, which should resemble `https://USERNAME.github.io/student-site/`, where `USERNAME` is your own GitHub username.

Congrats, you've published, or "deployed" the site! Anytime we save new versions of our website code to the repository's "main" branch, it will trigger a re-building of our hosted site.

> NOTE: sometimes it can take a few minutes for new changes to be reflected at the GitHub Pages URL.


### Downloading the Repository

Let's now download the website code so we can make changes and preview them locally before re-publishing.

From your repository's homepage on GitHub, click the green button to "Open with GitHub Desktop". Choose to save the repo in a location like your Desktop. Open the local repository in GitHub Desktop, if necessary.

### Making Changes

Open the repository with your text editor. Open the "about.html" file in your text editor.

Change some of the page's content, such as the student's name. Remember to save the file before previewing the changes.

### Previewing Changes

Open the repository with your operating system's file explorer / finder.

Right-click on the "index.html" page or any other to view its contents in the browser.

### Publishing Changes

Optionally repeat the process of making and previewing changes.

When you are satisfied with your changes, use the GitHub Desktop to make a "commit" (save a new version).

After making a commit, push your changes up to your remote repo (named "origin" by default).  This should trigger a re-build of your GitHub pages site.



### Visiting

Re-visit the GitHub Pages URL, and navigate to the "about" page, where you should see your changes.

Congratulations, you've published a website!
