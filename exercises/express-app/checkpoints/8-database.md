# Express App Exercise Part 8: Interfacing with a Database

Let's setup our own database and configure our web application to fetch data from there. Because SQL is not a prerequisite for this course, we'll use a NoSQL key-value storage option called Firestore from Google. Firestore is available via the Firebase suite of products.

## Database Setup

Follow the [Firestore Database Setup Guide](/notes/databases/firestore/setup.md) to create an example database and credentials to access it. Download the resulting service account credentials JSON file into the root directory of this repo, specifically naming it "google-credentials.json".

Add a new line to your local ".env" file to ignore this file from version control:

```sh
# this is the ".env" file ...

google-credentials.json

# ...
```

## Package Installation

We're going to use some firebase-related packages from Google to access the database, so let's install those now:

```sh
npm install firebase firebase-admin --save
```

See also the [`firebase-admin` package notes](/notes/javascript/packages/firebase-admin.md).

## Usage

### Firestore Service

After setting up the database and configuring the credentials file, we should be able to update our app to fetch data from the database.

First create a new file called "firestore-service.js" in a new "services subdirectory, and place the following contents inside:

```js
// this is the "services/firestore-service.js" file...

const { initializeApp, cert } = require('firebase-admin/app');
const { getFirestore } = require('firebase-admin/firestore');

const serviceAccountCreds = require('../google-credentials.json'); // assumes you downloaded the credentials file here

initializeApp({credential: cert(serviceAccountCreds)});

const db = getFirestore();

async function fetchProducts() {
    console.log("FETCHING PRODUCTS...")

    // see: https://googleapis.dev/nodejs/firestore/latest/CollectionReference.html#get
    const docs = await db.collection("products").get()
    console.log("DOCS:", docs.size)

    // see: https://googleapis.dev/nodejs/firestore/latest/QuerySnapshot.html
    // instead of returning the products as documents with separate ids and data
    // let's create a single object with both the id and the data
    // to make them easier to process and loop through later
    var products = []
    docs.forEach((doc) => {
        //console.log("DOC ID:", doc.id, "DATA", doc.data())
        var product = doc.data() // create a new object with the product info
        product["id"] = doc.id // merge the id with the object
        products.push(product)
    })
    //console.log("PRODUCTS:", products.length)
    return products
}

module.exports = {db, fetchProducts}
```

Here we are referencing the environment variables we setup earlier, and defining a function called `fetchProducts()` to fetch product documents from our database. We're also exporting this functionality so other local files can import it.

### Product Routes and Views

Let's update our app's routes and views to fetch the products from the database, and display them on a page.

Update the "app.js" file to configure some new product-related routes:

```js
// this is the "app.js" file...

// ...

var productsRouter = require('./routes/products'); // around line 15

// ...

app.use('/products', productsRouter); // around line 43

// ...

```

And create a new file called "products.js" in the "routes" directory to define the routing logic:

```js
// this is the "routes/products.js" file...

var express = require('express');
var router = express.Router();

const {fetchProducts} = require("../services/firestore-service")

router.get('/products', async function(req, res, next) {
    try {
        var products = await fetchProducts()

        res.render("products", {"products": products})
    } catch (error) {
        req.flash("danger", "OOPS, failed to fetch products.")
        res.redirect("/")
    }
})

router.post('/orders', function(req, res, next) {
    console.log("FORM DATA", req.body)
    var productId = req.body.productId
    var productName = req.body.productName
    var productPrice = req.body.productPrice
    // todo: maybe update the form / flow to ask the user for this info as well...
    //var userEmail = "customer@example.com"
    //var quantity = 1
    //var totalPrice = productPrice * quantity
    console.log(productId, productName, productPrice)
    console.log("TODO: ORDER A PRODUCT!")

    req.flash("warning", "Order sent successfully (TODO)!")
    res.redirect("/products")
})

module.exports = router;
```

Here we are saying that when a user visits the "/products" route, we will reference the `fetchProducts()` function we imported from the firebase service helper file, and pass the resulting products to the "products" page.

So let's create that products page now, called "products.ejs" in the "views" directory:

```html
<!-- this is the "views/products.ejs " file... -->

<h1>Products</h1>

<p className="lead">Browse products and services...</p>

<!--
    BOOTSTRAP GRID
    https://getbootstrap.com/docs/5.0/layout/grid/#row-columns
-->
<div class="container">
    <div class="row">
    <% products.forEach(function(product){ %>
        <div class="col">
            <!--
                BOOTSTRAP CARD
                https://getbootstrap.com/docs/5.0/components/card/
            -->
            <div class="card" style="margin-bottom: 2em;">
                <img src="<%= product['url'] %>" class="card-img-top" alt="photo of <%= product['name'] %>">
                <div class="card-body">
                    <h5 class="card-title"><%= product["name"] %></h5>
                    <p class="card-text"><%= product["description"] %></p>

                    <form action="/orders" method="POST">
                        <input type="hidden" name="productId" value="<%= product['id'] %>">
                        <input type="hidden" name="productName" value="<%= product['name'] %>">
                        <input type="hidden" name="productPrice" value="<%= product['price'] %>">
                        <button class="btn btn-primary">Order Now!</button>
                    </form>
                </div>
            </div>
        </div>
    <% }) %>
    </div>
</div>
```

Notice how we are using some EJS to loop through the products and display some info about each.

Finally, let's add a nav link to this products page, by adding the following contents to the "layout.ejs" file in the "views" directory:

```html
<!-- this is the "views/layout.ejs " file... -->

<li class="nav-item">
    <a class="nav-link" href="/products">Products</a>
</li>

```


Alright, now we're ready to see if our app works. Restart the server as necessary, preview your app in the browser, navigate to the products page, and see the products displayed there.

Nice job, you've fetched data from the database!

Make a commit, with a message like "Fetch data from the database".

### Re-Deploying

We'll need to deploy the google credentials file to the server, so run these commands locally:

Configuring remote credentials file:

```sh
heroku buildpacks:add https://github.com/s2t2/heroku-google-application-credentials-buildpack

# stores contents of local credentials file (e.g. "google-credentials.json")
# ... into an environment variable on the server
# ... for use in conjunction with the buildpack
heroku config:set GOOGLE_CREDENTIALS="$(< google-credentials.json)"
```

Next time you deploy, the products functionality should be working:

```sh
git push heroku main
```
