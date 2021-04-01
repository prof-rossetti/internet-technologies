# "Website Style" Exercise Walkthrough

## Instructions

### Preparing an HTML Document

Create a new HTML file with the following contents:

```` html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>Hello | My Site</title>
  </head>
  <body>
    <h1>Hello World</h1>

    <p>Welcome to my site.</p>

    <div>
      <p>Some paragraph text here!</p>

      <ol>
        <li>One</li>
        <li>Two</li>
        <li>Three</li>
      </ol>

      <p>Some more text at the bottom.</p>
    </div>
  </body>
</html>
````

Preview this page in a browser to see it is not styled.

### Inline Styles

Update the HTML page to use inline CSS styles, using content like the following:

```` html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>Hello | My Site</title>
  </head>
  <body>
    <h1 style="font-size:48px; color: red;">Hello World</h1>

    <p style="font-family: monospace; color: '#ccc';">Welcome to my site.</p>

    <div style="border: 2px solid #000;">
      <p style="font-family: monospace; color: '#ccc';">Some paragraph text here!</p>

      <ol style="list-style:none;">
        <li style="display: inline;">One</li>
        <li style="display: inline;">Two</li>
        <li style="display: inline;">Three</li>
      </ol>

      <p style="font-family: monospace; color: 'red';">Some more text at the bottom.</p>
    </div>
  </body>
</html>
````

Preview this page in a browser to see the styles applied to the document.

![a screenshot of the aforementioned styles](example-style.png)

This version of the HTML file looks messier and harder to read than before. The styles are mixed-in with the structure, and neither is easy to distinguish from the other. We also see the same style declarations duplicated across multiple elements. We can remove this duplication by using a "stylesheet" to apply the same styles to specified elements (see next section).

### Internal Stylesheet

Update the HTML page to use an internal stylesheet, using content like the following:

```` html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>Hello | My Site</title>
    <style media="screen">

      h1 {
        font-size:48px;
        color: red;
      }

      p {
        font-family: monospace;
        color: '#ccc';
      }

      div#my-divider {
        border: 2px solid #000;
        height: 300px;
        width: 300px;
      }

      ol { list-style:none; }

      li.horizontal { display: inline; }

      .bottom { color:red; }

    </style>
  </head>
  <body>
    <h1>Hello World</h1>

    <p>Welcome to my site.</p>

    <div id="my-divider">
      <p>Some paragraph text here!</p>

      <ol>
        <li class="horizontal">One</li>
        <li class="horizontal">Two</li>
        <li class="horizontal">Three</li>
      </ol>

      <p class="bottom">Some more text</p>
    </div>
  </body>
</html>
````

Preview this page in a browser to see the document is styled the same as before.

This version of the HTML file is still a bit busy, with all those style declarations at the top. We can simplify our document even further by separating the style declarations into a different file (see next section).

### External Stylesheet (Local)

Update the HTML page to use an internal stylesheet, using content like the following:

```` html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>Hello | My Site</title>
    <link rel="stylesheet" type="text/css" href="assets/styles/my-style.css">
  </head>
  <body>
    <h1>Hello World</h1>

    <p>Welcome to my site.</p>

    <div id="my-divider">
      <p>Some paragraph text here!</p>

      <ol>
        <li class="horizontal">One</li>
        <li class="horizontal">Two</li>
        <li class="horizontal">Three</li>
      </ol>

      <p class="bottom">Some more text</p>
    </div>
  </body>
</html>
````

You'll notice the HTML `<link>` element references a CSS file called "my-style.css" nested inside some subdirectories called "assets" and "styles" respectively. Let's use the text editor to create those subdirectories and the CSS file, and place the existing style declarations inside:

```` css

/* THIS IS MY STYLESHEET (e.g. "assets/styles/my-style.css") */

h1 {
  font-size:48px;
  color: red;
}

p {
  font-family: monospace;
  color: '#ccc';
}

div#my-divider {
  border: 2px solid #000;
  height: 300px;
  width: 300px;
}

ol { list-style:none; }

li.horizontal { display: inline; }

.bottom { color:red; }

````

Preview this page in a browser to see the document is styled the same as before.

This approach results in files that are easier to read and more organized than the previous approaches. It is also more organized in the sense that the structural logic is separated from the style logic. This approach also allows us to reference the same stylesheet across multiple different HTML pages.

### External Stylesheet (Hosted)

In addition to, or instead of using our own stylesheets, we can leverage those from third party front end development frameworks like Twitter Bootstrap.

Refer to [Bootstrap CDN]() for guidance.

You might end up with something like the following example:

```` html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>Hello | My Site</title>

    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.0-beta3/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-eOJMYsd53ii+scO/bJGFsiCZc+5NDVN2yr8+0RDqr0Ql0h+rP48ckxlpbzKgwra6" crossorigin="anonymous">

    <link rel="stylesheet" type="text/css" href="assets/styles/my-style.css">
  </head>
  <body>
    <h1>Hello World</h1>

    <p class="lead">Welcome to my site.</p>

    <div id="my-divider">
      <p>Some paragraph text here!</p>

      <ol>
        <li class="horizontal">One</li>
        <li class="horizontal">Two</li>
        <li class="horizontal">Three</li>
      </ol>

      <p class="bottom">Some more text</p>

      <button>Button One</button>
      <button type="button" class="btn btn-default">Button Two</button>
      <button type="button" class="btn btn-primary">Button Three</button>
      <button type="button" class="btn btn-lg btn-danger">Button Four</button>

    </div>
  </body>
</html>
````

![a screenshot of bootstrap styles](example-bootstrap-style.png)


Read Twitter Bootstrap to style your site as desired! Refer to [Bootstrap Components](http://getbootstrap.com/components/) for more documentation and examples.
