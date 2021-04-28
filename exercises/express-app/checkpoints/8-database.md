# Express App Exercise Part 8: Interfacing with a Database

Let's setup our own database and configure our web application to fetch data from there. Because SQL is not a prerequisite for this course, we'll use a NoSQL key-value storage option called Firestore from Google. Firestore is available via the Firebase suite of products.

Follow the "Setup" section below to setup the database and configure the local repo with credentials to access it, then follow the "Usage" section to update the web application code.

## Setup

### Firebase Setup

Visit https://console.firebase.google.com/ to **create a new Firebase project**. When you create the project:

  1. Choose an existing Google Analytics account or create a new one.
  2. Enable the setting to automatically create a new property in this account.

Click the gear icon to visit the "Project Settings" page, locate the "Your Apps" section, and **create a Web App**, or use an existing one. When you create the app,  you'll see its **Firebase SDK credentials**. Use these values for the `FIREBASE_` environment variables (see "Environment Variables" section below).

> FYI: you can find the credentials anytime by visiting the app's settings page, finding the "Firebase SDK snippet", and clicking "Config".

### Firestore Database Setup

Follow [this guide](https://firebase.google.com/docs/firestore/quickstart#create) (just the "Create a Cloud Firestore database" section), to create a Firestore database for the Firebase project you just created. When you create the database, "start in test mode".

#### Products Collection

After the database has been created, create a new collection called "products" with a number of documents inside. Create each document using an auto-generated `id` attribute, as well as the attributes `name` (string), `description` (string), `price` (number) and `url` (string). Populate the documents based on the following examples:

name | description | price | url
--- | --- | --- | ---
Strawberries | Juicy organic strawberries. | 4.99 | https://picsum.photos/id/1080/360/200
Cup of Tea | An individually-prepared tea or coffee of choice. | 3.49 | https://picsum.photos/id/225/360/200
Textbook | It has all the answers. | 129.99 | https://picsum.photos/id/24/360/200

#### Orders Collection

Also create a new collection called "orders", with the following attributes:

  + `id` (auto-generated)
  + `userEmail` (string)
  + `productId` (string)
  + `quantity` (number)
  + `totalPrice` (number)
  + `timestamp` (number)


### Environment Variables

You should already have a ".env" file in the root directory. Place the following contents inside, specifying your own credentials you obtained from the Firebase console (see "Firebase Setup" step above):

```sh
# this the ".env" file...

#
# FIREBASE
#

REACT_APP_FIREBASE_API_KEY="_______"
REACT_APP_FIREBASE_AUTH_DOMAIN="my-project-123.firebaseapp.com"
REACT_APP_FIREBASE_PROJECT_ID="my-project-123"
REACT_APP_FIREBASE_STORAGE_BUCKET="my-project-123.appspot.com"
REACT_APP_FIREBASE_MESSAGING_SENDER_ID="_______"
REACT_APP_FIREBASE_APP_ID="_______"
#REACT_APP_FIREBASE_MEASUREMENT_ID="G-XXXXXXXXXX"
REACT_APP_FIREBASE_DATABASE_URL="https://my-project-123.firebaseio.com"
```

### Package Installation


We're going to use some firebase-related packages from Google to access the database, so let's install those now:

```sh
npm install firebase firebase-admin --save
```

References:

  + https://www.npmjs.com/package/firebase
  + https://www.npmjs.com/package/firebase-admin


## Usage

### Firebase Service

After setting up the database and configuring environment variables, we should be able to update our app to fetch data from the database.

First create a new file called "firebase-service.js" in the root directory, and place the following contents inside:

```js
// this is the "firebase-service.js" file...

const firebase = require("firebase/app")
require("firebase/firestore")
require("dotenv").config() // use environment variables defined in the ".env" file

const firebaseConfig = {
    apiKey: process.env.FIREBASE_API_KEY,
    authDomain: process.env.FIREBASE_AUTH_DOMAIN,
    databaseURL: process.env.FIREBASE_DATABASE_URL,
    projectId: process.env.FIREBASE_PROJECT_ID,
    storageBucket: process.env.FIREBASE_STORAGE_BUCKET,
    messagingSenderId: process.env.FIREBASE_MESSAGING_SENDER_ID,
    appId: process.env.FIREBASE_APP_ID
}
//console.log("FIREBASE CONFIG", firebaseConfig)

const app = firebase.initializeApp(firebaseConfig)

const db = firebase.firestore(app)

async function fetchProducts() {
    console.log("FETCHING PRODUCTS...")

    // https://googleapis.dev/nodejs/firestore/latest/CollectionReference.html#get
    const docs = await db.collection("products").get()
    console.log("DOCS:", docs.size)

    // https://googleapis.dev/nodejs/firestore/latest/QuerySnapshot.html
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

module.exports = {firebaseConfig, app, db, fetchProducts}
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

const {fetchProducts} = require("../firebase-service")

router.get('/', async function(req, res, next) {
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
    console.log("TODO: ORDER PRODUCT", productId, productName, productPrice)

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
                <img src="<%= product['image_url'] %>" class="card-img-top" alt="photo of <%= product['name'] %>">
                <div class="card-body">
                    <h5 class="card-title"><%= product["name"] %></h5>
                    <p class="card-text"><%= product["description"] %></p>
                    <form action="/products/orders" method="POST">
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
<!-- ... -->
<li class="nav-item">
    <a class="nav-link" href="/products">Products</a>
</li>
<!-- ... -->
```


Alright, now we're ready to see if our app works. Restart the server as necessary, preview your app in the browser, navigate to the products page, and see the products displayed there.

Nice job, you've fetched data from the database.

## Further Exploration

Right now when a user clicks to order a product, there is just some placeholder functionality. But can you update the application code to actually store orders in the database?

Make your own decisions about what data to capture from the user, and how. For example, we might want to display a modal or intermediary form to ask the user for their email and the number of products to order.

HINT: you might want to add a function like this to the "firebase-service.js" file:

```js
// this is the "firebase-service.js" file...
// ...
async function createOrder(newOrder) {
    //
    // FYI: newOrder param should look like:
    //
    // {
    //   "userEmail": "hello@example.com",
    //   "productID": "klmnopq",
    //   "quantity": 2,
    //   "totalPrice": 6.99
    // }
    //
    newOrder["timestamp"] = parseInt(Date.now().toFixed())
    console.log("NEW ORDER:", newOrder)

    // see: https://googleapis.dev/nodejs/firestore/latest/CollectionReference.html
    var ordersRef = db.collection("orders")

    // see: https://firebase.google.com/docs/database/admin/save-data
    await ordersRef.add(newOrder)

    return newOrder
}

module.exports = {firebaseConfig, app, db, fetchProducts, createOrder}
```
