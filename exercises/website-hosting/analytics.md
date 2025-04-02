
# Website Analytics Exercise

## Prerequisites

  + Complete the [Website Hosting Exercise](/exercises/website-hosting/exercise.md) and ensure your website is already hosted.
  + Sign up for a [Google Analytics](https://analytics.google.com) account.


## Learning Objectives

  + Configure your hosted website to track pageviews and user events.

## Instructions

### Configure Google Analytics

Login to your [Google Analytics](https://analytics.google.com/analytics/web/) account.

From the admin settings (gear icon bottom left), create a new Web Property, called something like "Student Site" or "Analytics Exercise". If asked about business objectives, choose "Understand web and/or app traffic" and "View user engagement & retention".

From the "Start collecting data" page or the Web Property's settings page, set up a "Web" "Data Stream". Specify the URL to your hosted GitHub Pages site. Keep enhanced measurement turned on.

From the "Set up a Google tag" page, copy the provided code snippet, which resembles something like the following (replacing "G-XXXXXXXX" with your own unique measurement identifier):

```html
<!-- Google tag (gtag.js) -->
<script async src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXX"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());

  gtag('config', 'G-XXXXXXXX');
</script>
```

### Configure the Website

#### Tracking Pageviews

As instructed, add your provided snippet to to each of your website's HTML files, immediately after the opening <head> tag. In other words, it should be the first thing inside the <head> section.

See also this guide about [Adding the Google Analytics Tag to your site](https://developers.google.com/analytics/devguides/collection/ga4), which says "This code should appear immediately after the opening <head> tag. You need only one global snippet per page."

Save all the files, commit your changes, and push them to GitHub to trigger a re-build of your GitHub Pages site.

Then visit the hosted site and ask some friends to visit as well, and measure your pageviews in Google Analytics.

> NOTE: in some cases, you may need to wait around 24-48 hours for the data to start collecting.

> NOTE: page views and events will not be triggered by visitors who have disabled JavaScript via their browser settings or plugins.

#### Tracking Events

> NOTE: sending events is a bit of an advanced use case, so beginners can feel free to skip.

If you would like to send additional "event" data to Google Analytics, follow this [Sending Events Guide](https://developers.google.com/analytics/devguides/collection/protocol/ga4/sending-events?client_type=gtag).

See also the [About events](https://support.google.com/analytics/answer/9322688) page.
