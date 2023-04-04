
# Website Analytics Exercise

## Prerequisites

  + [Website Hosting Exercise](/exercises/website-hosting/exercise.md)
  + Sign up for a [Google Analytics](https://analytics.google.com) account.

## Learning Objectives

  + Configure your website to track pageviews and user events.

## Instructions

### Configure Google Analytics

Login to your [Google Analytics](https://analytics.google.com/analytics/web/) account.

From the admin settings (see gear icon bottom left), create a new Web Property, called something like "Student Site".

From the Web Property settings, set up a "Web" "Data Stream". Specify the URL to your hosted GitHub Pages site. Keep enhanced measurement turned on.

Locate your data stream's "Measurement Id" (e.g. "G-XXXXXXXX"). Click "view tag instructions" to reveal the configuration code you'll need in the next step.

### Configure the Website

#### Tracking Pageviews

As instructed, add a snippet like this to each of your website's HTML files, where `MEASUREMENT_ID` refers to the Measurement Id you obtained in the previous step. See also this guide about [Adding the Google Analytics Tag to your site](https://developers.google.com/analytics/devguides/collection/ga4), which says "This code should appear immediately after the opening <head> tag. You need only one global snippet per page."

```html
<!-- Global site tag (gtag.js) - Google Analytics -->
<script async src="https://www.googletagmanager.com/gtag/js?id=YOUR_MEASUREMENT_ID"></script>
<script>
    window.dataLayer = window.dataLayer || [];
    function gtag(){dataLayer.push(arguments);}
    gtag('js', new Date());

    gtag('config', 'YOUR_MEASUREMENT_ID');
</script>
```

Save the file, commit your changes, and push them to GitHub to trigger a re-build of your GitHub Pages site. Visit the site and ask some friends to visit as well, and measure your pageviews in Google Analytics.

#### Tracking Events

To track events, we'll add a JavaScript snippet like the following examples / templates.

```js
// event template:
gtag('event', '<type>', {<parameters>});
```

```js
// event template / example:
gtag('event', '<type>', {
  'event_category': '<category>',
  'event_label':' <label>',
  'value': '<value>'
});
```

See also: [Sending Google Analytics Events](https://developers.google.com/analytics/devguides/collection/gtagjs/events), for more info, and [Anatomy of an Event](https://support.google.com/analytics/answer/1033068#Anatomy), which describes some of the event categories.

We'll learn more about website interactivity in a later lesson, but for now, let's add the following JavaScript to the bottom of the body of the "experience.html" page:


```html
<script type="text/javascript">

    // referencing an HTML button element by its identifier:
    var resumeButton = document.getElementById("download-resume")

    // defining a reusable function:
    function handleClick() {
        console.log("YOU CLICKED ME!")

        // send event to GA
        gtag("event", "resume_download")
    }

    // triggering the function when the button is clicked:
    resumeButton.addEventListener("click", handleClick, false)

</script>
```

Save the file, commit your changes, and push them to GitHub to trigger a re-build of your GitHub Pages site. Visit the site and click the button and see the resulting events logged in Google Analytics.

> NOTE: it might take a day or two for events to start showing up in Google Analytics.
