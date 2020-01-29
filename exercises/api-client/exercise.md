# "API Client" Exercise

## Prerequisites

  + [Website Interactivity Exercise](/exercises/website-interactivity/exercise.md)
  + [APIs](https://github.com/prof-rossetti/intro-to-python/blob/master/notes/software/apis.md)

## Objectives

Use an HTML `form` element to send a "POST" HTTP request to a pre-configured API in order to create a new record in the API's database.

## Instructions

In your "website-interactivity" project, or in a new project called "api-client", create a new HTML file called "create_product.html" and paste the following contents inside:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Products Form</title>
  </head>
  <body>

    <h2>New Product Form</h2>
    <p>Please fill-in the form below...</p>

    <form action="https://web-app-starter-flask-sheets.herokuapp.com/products/create" method="POST">
      <label>Name:</label>
      <input type="text" name="product_name" placeholder="Product XYZ" value="Product XYZ">
      <br>

      <label>Department:</label>
      <select name="department">
        <option value="snacks">Snacks</option>
        <option value="beverages">Beverages</option>
        <option value="pantry">Pantry</option>
        <option value="frozen">Frozen</option>
      </select>
      <br>

      <label>Price:</label>
      <input type="number" step="0.01" min="0" name="price" value="4.99" >
      <br>

      <label>Available as of:</label>
      <input type="date" name="availability_date" value="2019-01-01">
      <br>

      <button>Submit</button>
    </form>

    <footer>
      <hr>
      <p>
        See: <a href="https://docs.google.com/spreadsheets/d/1_hisQ9kNjmc-cafIasMue6IQG-ql_6TcqFGpVNOkUSE/edit#gid=0">Google Sheet Database</a>
        and <a href="https://github.com/prof-rossetti/web-app-starter-flask-sheets/blob/6f16635b4ed627f318c18dc8eecf5b6ae15a6451/web_app/routes/products.py#L20-L37">API Source Code</a>
        and <a href="https://web-app-starter-flask-sheets.herokuapp.com/products">API</a>
      </p>
    </footer>
  </body>
</html>

```

Preview your website by either opening the HTML file with the browser, or navigating to your project directory from the command-line and starting up a local web server:

```sh
cd ~/Desktop/website-interactivity/
python -m http.server 8888
```

## Further Exploration

Create another HTML file called "list_products.html", and paste the following contents inside:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Products List</title>
  </head>
  <body>

    <h2>Products List</h2>
    <ul id="products-list"></ul>

    <footer>
      <hr>
      <p>
        See: <a href="https://groceries-api-csv.herokuapp.com/">API</a>
        and <a href="https://github.com/prof-rossetti/products-api-flask">API Source Code</a>
      </p>
    </footer>

    <script>

      var requestUrl = "https://groceries-api-csv.herokuapp.com/products"
      console.log("FETCHING PRODUCTS FROM", requestUrl)

      // TODO: fetch the products, and for each: append a new list item to the "products-list" element

    </script>
  </body>
</html>

```

Use the `fetch()` JavaScript function, as demonstrated in the [Dataviz Exercise](/exercises/website-interactivity/challenges.md), to issue a "GET" HTTP request to the pre-configured products API, using the specified request URL.

Then use JavaScript to dynamically create a list item (`li`) element to display the name of each product on the page!
