# The Formspree Service

The role of an [HTML Form](https://www.w3schools.com/html/html_forms.asp) is usually to send some data to a server somewhere. We could create our own server-side application to receive the data, or use a service like [Formspree](https://formspree.io/) to handle the data for us.
Formspree will forward data sent through a web form to an email address we configure.

## Usage

After creating a Formspree account and verifying your email address, use the Formspree interface to create a new project as desired, then click to create a new form. 

After doing so, you'll see some example code they're instructing you to add to your site, like the following (using your own unique endpoint i.e. `YOUR_ENDPOINT`):



```html
<!-- modify this form HTML and place wherever you want your form -->
<form action="https://formspree.io/f/YOUR_ENDPOINT" method="POST">
  <label>
    Your email:
    <input type="email" name="email">
  </label>
  
  <label>
    Your message:
    <textarea name="message"></textarea>
  </label>
  
  <!-- your other form fields go here -->
  
  <button type="submit">Send</button>
</form>

```

Add this code to your site (somewhere in the HTML page's `body`). Save the file and preview the form locally. Submit the form with some example inputs. Then check your email to see the values you submitted. Nice!

If you'd like to make your forms and input elements look better, try styling via [Bootstrap Forms](https://getbootstrap.com/docs/5.0/forms/overview/).
