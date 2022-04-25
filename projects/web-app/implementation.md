# Web App Project Implementation

> See: [The Web App Project](project.md)

## Instructions

Iteratively develop your project using version control practices. Save new versions of your source code as you reach key milestones.

If working in a group, each group member should ideally make significant contributions to the application's source code!

Include written instructions in the repo's README file to tell someone else how to download your code, setup the app, run the app locally, and deploy it. If connecting to third-party APIs or back-end databases, include instructions for how to set up the database, obtain credentials, etc.

If using secret credentials like API keys, the source code should ABSOLUTELY NOT contain those secret credentials. Instead, specify these credentials as [environment variables](/notes/environment-variables.md) inside a ".env" file in your repo's root directory, and use [the "dotenv" package](/notes/javascript/packages/dotenv.md) to read them indirectly from there.



## Submission Instructions

Submit the designated Google Form before the designated date, providing the URLs to your GitHub repository and hosted site.

## Evaluation

Web applications will be evaluated according to the [project requirements](project.md#requirements) and instructions set forth above, as summarized by the rubric below:

Category | Requirement | Weight
--- | --- | ---
Hosting | App is publicly accessible over the Internet (i.e. hosted via GitHub Pages, Heroku, or Firebase Hosting). | 10%
Structure | App has at least three navigable pages, with consistent navigation across all pages. | 10%
Style | App is reasonably well styled, and "responsive" when window is resized to a mobile device width. | 10%
Interactivity | App includes interactive features, like responding to button click events or web form submission. | 10%
Data Processing | App fetches data from a third-party API or back-end database. Ideally also sends data to a back-end database. | 10%
Content | App content is creative and unique. | 15%
Documentation | Repo contains a comprehensive README file with written setup instructions and usage commands. | 10%
Security | Excludes sensitive information and credentials from version control; uses server-side requests to protect secret credentials and/or user data as necessary. | 10%
Dev Process | Submitted via remote Git repository which reflects an incremental revision history, and contributions from ideally all team members. | 15%



This rubric is tentative, and may be subject to slight adjustments during the grading process.

If experiencing navigation or functionality error(s) while evaluating the app, evaluators are advised to reduce the grade by between 4% and 25%, depending on the circumstances and severity of the error(s).

In recognition of deliverables which exhibit functionality above and beyond the basic requirements, evaluators are encouraged to award between 4% and 15% "engagement points" to be applied as extra credit.
