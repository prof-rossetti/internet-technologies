# "Crunch the Data" Exercise

## Setup

Download or copy these HTML files locally (["gradebook.html"](gradebook.html), ["rideshare.html"](rideshare.html), ["social.html"](social.html)), ideally into the same local directory. Open them in the text editor, and preview them in the browser. Open the browser's inspection tools to view the JavaScript console, where you should see the data printed.

For each of the challenges, write more JavaScript at the bottom of the document to produce the desired results (usually printing or logging some calculated result). To test your code, save the document and refresh the page in the browser, and repeat until you see the desired result in the console.

## Challenges

### Challenge 1: Gradebook

Given the JavaScript variable called `gradebook` provided below, write JavaScript code which references that variable to perform each of the following tasks...

A) Print the date this data was downloaded (i.e. `"2021-06-05"`).

B) Print the number of students in the gradebook (i.e. `10`).

C) Loop through each student and print their grade, each on a new line.

D) Print the average grade (i.e. `83.64`).

E) Print the median grade (i.e. `87.6`).


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

A) Print a human-friendly message to denote the driver’s first name (i.e. `"Your driver is Danny"`).

B) Assuming stops can get added or removed at any time, print the number of stops this trip makes (i.e. `3`).

C) Assuming the stops will always be listed in ascending order of their stop sequence, and there will always be at least one stop, print the destination of the FIRST stop (i.e. `Madison Square"`).

D) Assuming the stops will always be listed in ascending order of their stop sequence, and there will always be at least one stop, but the number of stops may change at any time, print the destination of the LAST stop (i.e. `"Washington Square"`).

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
