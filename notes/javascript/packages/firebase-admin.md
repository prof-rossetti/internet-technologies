
# The `firebase-admin` Package

The `firebase-admin` package helps us fetch data from a a NoSQL key-value storage option called Firestore from Google. Firestore is available within the Firebase suite of products.

References:

  + [NPM Page](https://www.npmjs.com/package/firebase-admin)
  + [Source Code](https://github.com/firebase/firebase-admin-node#documentation)
  + [Docs](https://github.com/firebase/firebase-admin-node#documentation)

## Database Setup

Follow the [Firestore Database Setup Guide](/notes/databases/firestore/setup.md) to create an example database and credentials to access it. Download the resulting service account credentials JSON file into the root directory of your project's repo, specifically naming it "google-credentials.json".

## Installation

```sh
npm install firebase firebase-admin --save
```

## Usage

Finally, after setting up the database and configuring the local credentials file, you should be able to use code like this to fetch the products from the database:

```js
// this is a file like "my_script.js" file...

const { initializeApp, cert } = require('firebase-admin/app');
const { getFirestore } = require('firebase-admin/firestore');

// references the location where you downloaded the credentials file
const serviceAccountCreds = require('./google-credentials.json');

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

//fetchProducts()

//module.exports = {db, fetchProducts}
```
