
# Website Analytics Exercise

## Prerequisites

  + [Website Hosting Exercise](/exercises/website-hosting/exercise.md)
  + Sign up for a [Google Analytics](https://analytics.google.com) account.

## Learning Objectives

  + Configure your website to track pageviews and user events.

## Instructions

### Configure Google Analytics

Login to your Google Analytics account.

From the admin settings, create a new Web Property, called something like "Student Site".

From the Web Property settings, set up a "Web" "Data Stream". Use the GitHub Pages URL.

Locate your data stream's "Measurement Id" (e.g. "G-XXXXXXXX"). Click "global site tag" to reveal the configuration code you'll need in the next step.

### Configure the Website

#### Tracking Pageviews

As instructed, add the following snippet at the bottom of each of your website's HTML files:

```html
<!-- Global site tag (gtag.js) - Google Analytics -->
<script async src="https://www.googletagmanager.com/gtag/js?id=MEASUREMENT_ID"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());

  gtag('config', 'MEASUREMENT_ID');
</script>
```

See: [Add the Google Analytics Tag to your site](https://developers.google.com/analytics/devguides/collection/ga4), which says "This code should appear immediately after the opening <head> tag. You need only one global snippet per page."

Save the file, commit your changes, and push them to GitHub to trigger a re-build of your GitHub Pages site. Visit the site and ask some friends to visit as well, and measure your pageviews in Google Analytics.

#### Tracking Events

To track events, we'll add a JavaScript snippet like the following:

```js
gtag('event', <action>, {
  'event_category': <category>,
  'event_label': <label>,
  'value': <value>
});
```

See: [Sending Google Analytics Events](https://developers.google.com/analytics/devguides/collection/gtagjs/events), for more info, and [Anatomy of an Event](https://support.google.com/analytics/answer/1033068#Anatomy), which describes some of the event categories.

We'll learn more about website interactivity in a later lesson, but for now, just add the following JavaScript to the bottom of the body of the "experience.html" page:


```html
<script type="text/javascript">

    var resumeButton = document.getElementById("download-resume")

    function handleClick(event) {
        console.log("YOU CLICKED ME!")
        console.log(event.target)

        // send event to GA
        gtag("event", "resume_download")
    }

    resumeButton.addEventListener("click", handleClick, false)

</script>
```

Save the file, commit your changes, and push them to GitHub to trigger a re-build of your GitHub Pages site. Visit the site and click the button and see the resulting events logged in Google Analytics.
