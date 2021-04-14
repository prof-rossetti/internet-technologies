# "Crunch the Data" Exercise

## Setup

Download or copy these HTML files (["gradebook.html"](gradebook.html), ["rideshare.html"](rideshare.html), ["social.html"](social.html), ["stocks.html"](stocks.html)), into the same local directory (perhaps the same one you used for the Website Interactivity exercise). Open them in the text editor, and preview each in the browser. View the browser's inspection tools to reveal the JavaScript console, where you should see the data printed.

For each of the challenges, write more JavaScript at the bottom of the document to produce the desired results (usually printing or logging some calculated result). To test your code, save the document and refresh the page in the browser, and repeat until you see the desired result in the console.

## Challenges

### Challenge 1: Gradebook

Given the JavaScript variable called `gradebook` provided below, write JavaScript code which references that variable to perform each of the following tasks...

A) Log the date this data was downloaded (i.e. `"2021-06-05"`).

B) Log the number of students in the gradebook (i.e. `10`).

C) Loop through each student and log their grade, each on a new line.

D) Log the average grade (i.e. `83.64`).

E) Log the median grade (i.e. `87.6`). HINT: it may be helpful to leverage a third-party library like [d3.median()](https://github.com/d3/d3-array#median)


```js
var gradebook = {
  "downloadDate": "2021-06-05",
  "professorId": 123,
  "students":[
    {"studentId": 1, "name": "Student 1", "finalGrade": 76.7},
    {"studentId": 2, "name": "Student 2", "finalGrade": 85.1},
    {"studentId": 3, "name": "Student 3", "finalGrade": 50.3},
    {"studentId": 4, "name": "Student 4", "finalGrade": 89.8},
    {"studentId": 5, "name": "Student 5", "finalGrade": 97.4},
    {"studentId": 6, "name": "Student 6", "finalGrade": 75.5},
    {"studentId": 7, "name": "Student 7", "finalGrade": 87.2},
    {"studentId": 8, "name": "Student 8", "finalGrade": 88.0},
    {"studentId": 9, "name": "Student 9", "finalGrade": 93.9},
    {"studentId": 10, "name": "Student 10", "finalGrade": 92.5}
  ]
}
```

> Further Exploration: also write JavaScript to create new HTML elements from this data and display them within the `div#gradebook-app` element. For example, try displaying a list or table of students.

### Challenge 2: Rideshare

Given the JavaScript variable called `trip` provided below, write JavaScript code which references that variable to perform each of the following tasks...

A) Log a human-friendly message to denote the driver’s first name (i.e. `"Your driver is Danny"`).

B) Assuming stops can get added or removed at any time, log the number of stops this trip makes (i.e. `3`).

C) Assuming the stops will always be listed in ascending order of their stop sequence, and there will always be at least one stop, but the number of stops may change at any time, log the destination of the FIRST stop (i.e. `Madison Square"`).

D) Assuming the stops will always be listed in ascending order of their stop sequence, and there will always be at least one stop, but the number of stops may change at any time, print the destination of the LAST stop (i.e. currently `"Washington Square"`).

E) Loop through each of the trip’s stops and print that stop’s passenger name, one at a time (i.e. `"Vishal"`, then `"Clara"`, then `"Lee"`, each on a separate line):

```js
var trip = {
    "driver": {
        "first_name": "Danny",
        "last_name": "Dreyfus",
        "avg_rating": 3.6,
        "total_rides": 950
    },
    "vehicle": {
        "make": "Tesla",
        "model": "Cybertruck",
        "year": 2021,
        "color": "silver"
    },
    "rideshare": true,
    "pickup_location": "Grand Central Terminal",
    "stops": [
        {"sequence": 1, "passenger": "Vishal", "destination": "Madison Square", "fare": 3.99},
        {"sequence": 2, "passenger": "Clara", "destination": "Union Square", "fare": 5.99},
        {"sequence": 3, "passenger": "Lee", "destination": "Washington Square", "fare": 7.99}
    ]
}
```

> Further Exploration: also write JavaScript to create new HTML elements from this data and display them within the `div#rideshare-app` element. For example, try displaying an ordered list of stops.

### Challenge 3: Social Media

Given the JavaScript variable called `tweets` provided below, write JavaScript code which references that variable to perform each of the following tasks...

A) Print the screen name of the user who authored the first tweet (i.e. `"sandwhoa"`).


B) Of all the tweets which include the phrase `"@sandwhoa"` in their full text, print the screen name of the user who authored that tweet, each on a separate line (i.e. `"person2"`, then `"person3"`).

C) Of all the tweets which include the phrase `"@sandwhoa"` in their full text, determine which tweet has the greatest number of likes, and then print the screen name of the user who authored that tweet (i.e. `"person3"`). FYI: Assume the tweet order can change at any time and has no relationship with the number of likes.

```js
var tweets = [
    {
        "id": 100200297,
        "full_text": "Look at this delicious sandwich!",
        "img_url": "https://sandwhoa.com/sandwich.png",
        "user": {"screen_name": "sandwhoa", "followers": 5000},
        "likes_count": 150
    },
    {
        "id": 100200298,
        "full_text": "I love sandwiches",
        "img_url": null,
        "user": {"screen_name": "person1", "followers": 100},
        "likes_count": 5
    },
    {
        "id": 100200299,
        "full_text": "@sandwhoa yumm...",
        "img_url": null,
        "user": {"screen_name": "person2", "followers": 200},
        "likes_count": 10
    },
    {
        "id": 100200300,
        "full_text": "@sandwhoa that sandwich looks amazing!!",
        "img_url": null,
        "user": {"screen_name": "person3", "followers": 300},
        "likes_count": 35
    },
    {
        "id": 100200301,
        "full_text": "I ate a great sandwich today",
        "img_url": null,
        "user": {"screen_name": "person4", "followers": 400},
        "likes_count": 50
    }
]
```

> Further Exploration: also write JavaScript to create new HTML elements from this data and display them within the `div#social-app` element. For example, try displaying the newsfeed in a table or list, or with cards.



### Challenge 4: Stocks

Given the JavaScript variable called `stockData` provided below, write JavaScript code which references that variable to perform each of the following tasks...

A) Log the stock symbol (i.e. `"MSFT"`).

B) Log the number of days included in the time series data (i.e. `4`). HINT: the time series is an Object, not a List, so we might need to start using some of these [Object methods](https://github.com/prof-rossetti/internet-technologies/blob/main/notes/javascript/datatypes/objects.md#object-methods) to reference an array of just the keys, an array of just the values, or an array of the key-value pairs.

C) Loop through each day, and log the date as well as that day's adjusted closing price, each on a new line.

D) Log the latest adjusted closing price (i.e. `258.49`). NOTE: let's assume the latest day is the first one provided in the time series, but that the date value will change over time. 

F) Assemble a new list of just the dates, in ascending chronological order, then log that list (i.e. `["2021-04-08", "2021-04-09", "2021-04-12", "2021-04-13" ]`).

E) Assemble a new list of just the daily adjusted closing prices, in ascending chronological order, then log that list (i.e. `[253.25, 255.85, 255.91, 258.49]`).


```js
var stockData = {
    "Meta Data": {
        "1. Information": "Daily Time Series with Splits and Dividend Events",
        "2. Symbol": "MSFT",
        "3. Last Refreshed": "2021-04-13",
        "4. Output Size": "Compact",
        "5. Time Zone": "US/Eastern"
    },
    "Time Series (Daily)": {
        "2021-04-13": {
            "1. open": "257.2573",
            "2. high": "259.19",
            "3. low": "256.83",
            "4. close": "258.49",
            "5. adjusted close": "258.49",
            "6. volume": "23837469",
            "7. dividend amount": "0.0000",
            "8. split coefficient": "1.0"
        },
        "2021-04-12": {
            "1. open": "254.71",
            "2. high": "257.67",
            "3. low": "254.62",
            "4. close": "255.91",
            "5. adjusted close": "255.91",
            "6. volume": "27148668",
            "7. dividend amount": "0.0000",
            "8. split coefficient": "1.0"
        },
        "2021-04-09": {
            "1. open": "252.87",
            "2. high": "255.99",
            "3. low": "252.44",
            "4. close": "255.85",
            "5. adjusted close": "255.85",
            "6. volume": "24326833",
            "7. dividend amount": "0.0000",
            "8. split coefficient": "1.0"
        },
        "2021-04-08": {
            "1. open": "252.77",
            "2. high": "254.139",
            "3. low": "252.0",
            "4. close": "253.25",
            "5. adjusted close": "253.25",
            "6. volume": "23625197",
            "7. dividend amount": "0.0000",
            "8. split coefficient": "1.0"
        }
    }
}
```

> Further Exploration: also write JavaScript to create new HTML elements from this data and display them within the `div#stocks-app` element. For example, try displaying the stock symbol and the latest closing price.


