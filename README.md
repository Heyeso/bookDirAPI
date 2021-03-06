# Books Directory REST API

This is a basic library REST API that gets, adds, update and deletes books in and from a database.

## Install the npm and dependencies

- run `npm i`

## Run the API

- run `npm start`
- or run `node server.js` file in `%FOLDER%/src/server.js`on the command-line to start the server.

# REST API

(Preferable) Use Postman to fetch from the API.

## Get all books

### Request

`GET /book`

    `http://localhost:{PORT}/:api_key/book`

### Response

    ```
    [
        {
    		"_id": "60ac0001d677c41cdf3fb6a8",
    		"isbn": "9781593275846",
    		"title": "Eloquent JavaScript, Second Edition",
    		"author": "Marijn Haverbeke",
    		"publisher": "No Starch Press",
    		"pages": 472,
    		"publish": "2014-12-14T00:00:00.000Z"
    	}
    ]
    ```

## Get a specific book

### Request

`GET /book/:title/:isbn?`

    `http://localhost:{PORT}//:api_key/book/Eloquent%20JavaScript,%20Second%20Edition`

### Response

    ```
    [
        {
    		"_id": "60ac0001d677c41cdf3fb6a8",
    		"isbn": "9781593275846",
    		"title": "Eloquent JavaScript, Second Edition",
    		"author": "Marijn Haverbeke",
    		"publisher": "No Starch Press",
    		"pages": 472,
    		"published": "2014-12-14T00:00:00.000Z",
    		"publish": "2021-06-10T17:45:04.729Z"
    	}
    ]
    ```

## Create and Add a book

### Request

`POST /book/add`

    `http://localhost:{PORT}/:api_key/book/add`
    ```
    Body: {
    		"isbn": "9781575846111",
    		"title": "The End",
    		"author": "Abdulsalam Odetayo",
    		"publisher": "Heyeso",
    		"pages": 421,
    	}
    ```

### Response

    ```
    [
        {
    		"_id": "60c165676c30210ff0dffd81",
    		"isbn": "9781575846111",
    		"title": "The End",
    		"author": "Abdulsalam Odetayo",
    		"publisher": "Heyeso",
    		"pages": 421,
    		"publish": "2021-06-10T01:05:43.270Z"
    	}
    ]
    ```

## Get a non-existent Book

### Request

`GET /book/:title/:isbn?`

    `http://localhost:{PORT}//:api_key/book/:title/:isbn?`


### Response

    	<body> Book does not exist <body>

## Change a book

### Request

`PUT /book/update`

    `http://localhost:{PORT}/:api_key/book/update`

    ```
    Body: {
            "isbn": "9781575846111",
    		"title": "The Beginning",
    		"pages": 41,
    	}
    ```

### Response

    ```
    [
        {
    		"_id": "60c165676c30210ff0dffd81",
    		"isbn": "9781575846111",
    		"title": "The Beginning",
    		"author": "Abdulsalam Odetayo",
    		"publisher": "Heyeso",
    		"pages": 41,
    		"publish": "2021-06-10T01:05:43.270Z"
    	}
    ]
    ```

## Attempt to change a Book using invalid params

### Request

`PUT /book/update`

    `http://localhost:{PORT}/:api_key/book/update`

    ```
    Body: {
        	"isbn": "9781575846111",
    		"second": "The Beginning",
    		"page": 41,
    	}
    ```

### Response

    ```
    [
        {
    		"_id": "60c165676c30210ff0dffd81",
    		"isbn": "9781575846111",
    		"title": "The End",
    		"author": "Abdulsalam Odetayo",
    		"publisher": "Heyeso",
    		"pages": 421,
    		"publish": "2021-06-10T01:05:43.270Z"
    	}
    ]
    ```

## Delete a Thing

### Request

`DELETE /book/delete`

    `http://localhost:{PORT}/:api_key/book/delete`
    ```
    Body: {
        	"isbn": "9781575846111"
    	}
    ```

### Response

    ``` 
    DELETED
    ```

## Get deleted Thing

### Request

`GET /book`

    `http://localhost:{PORT}/:api_key/book`
    ```
        Body: {
                "isbn": "9781575846111",
                "title": "The End"
            }
     ```
### Response

```
<body> Book does not exist <body>
```
