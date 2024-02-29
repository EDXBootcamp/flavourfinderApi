# Flavour Finder API Documentation

This documentation outlines the RESTful API endpoints available for managing restaurant data.

## Base URL

The base URL for accessing the Restaurant API is:

```
https://flavourfinder.tjthouhid.com
```

## Authentication

All endpoints require an API key for authentication. Pass the API key as a query parameter named `api_key` in the request URL.

## Endpoints

### 1. Add a Restaurant

Add a new restaurant to the database.

- **URL**: `/restaurent.php`
- **Method**: `POST`
- **Parameters**:
  - `restaurant_name` (required): The name of the restaurant.
  - `restaurant_type` (optional): The type of restaurant.
  - `city` (required): The city where the restaurant is located.
  - `country` (required): The country where the restaurant is located.
  - `image` (required): file jpg/jpeg/png.
- **Example**:

```javascript
axios.post('https://flavourfinder.tjthouhid.com/restaurent.php', {
    restaurant_name: 'New Restaurant',
    restaurant_type: 'Cuisine Type',
    city: 'City Name',
    country: 'Country Name'
}, {
    params: {
        api_key: 'your_api_key'
    }
})
.then(response => {
    console.log(response.data);
})
.catch(error => {
    console.error(error);
});
```
- **Response**:

```json
{
    "success": true,
    "message": "Restaurant added successfully"
}
```

### 2. Get All Restaurants

Retrieve a list of all restaurants stored in the database.

- **URL**: `/restaurent.php`
- **Method**: `GET`
- **Parameters**:
    - `restaurant_name` (optional): The name of.
    - `city` (optional): The city of restaurant.
    - `country` (optional): The country of restaurant.
- **Example**:

```javascript
axios.get('https://flavourfinder.tjthouhid.com/restaurent.php', {
    params: {
        api_key: 'your_api_key'
    }
})
.then(response => {
    console.log(response.data);
})
.catch(error => {
    console.error(error);
});
```
- **Response**:

```json
{
    "success": true,
    "restaurants": [
        {
            "restaurant_id": "1",
            "restaurant_name": "My Restaurent",
            "restaurant_type": "Chinese",
            "city": "Bedford",
            "country": "England",
            "image": "https://url..",
            "total_reviews": "3",
            "average_rating": "4.00000"
        },
        {
            "restaurant_id": "2",
            "restaurant_name": "My Restaurent 2",
            "restaurant_type": "Chinese",
            "city": "Bedford",
            "country": "England",
            "image": "https://url..",
            "total_reviews": "0",
            "average_rating": null
        }
    ]
}
```


### 3. Get Single Restaurant

Retrieve data for a single restaurant by its ID.

- **URL**: `/restaurent.php?restaurant_id={id}`
- **Method**: `GET`
- **Parameters**:
 - `restaurant_id` (required): The ID of the restaurant to retrieve.
- **Example**:

```javascript
const restaurantId = 123; // Replace with the desired restaurant ID
axios.get(`https://flavourfinder.tjthouhid.com/restaurent.php?restaurant_id={id}`, {
    params: {
        api_key: 'your_api_key'
    }
})
.then(response => {
    console.log(response.data);
})
.catch(error => {
    console.error(error);
});

```

- **Response**:

```json
{
    "success": true,
    "restaurant": {
        "restaurant_id": 1,
        "restaurant_name": "My Restaurent",
        "restaurant_type": "Chinese",
        "city": "Bedford",
        "country": "England",
        "total_reviews": 3,
        "average_rating": "4.00000"
    }
}
```

### 4. Add a Reviews

Add a new review to the restaurent.

- **URL**: `/reviews.php`
- **Method**: `POST`
- **Parameters**:
  - `restaurant_id` (required): The id of the restaurant.
  - `reviewer_name` (required): The name of the reviewer.
  - `reviewer_email` (required): The email of the reviewer.
  - `comment` (optional): Review text detail.
  - `star_rating` (required): star rating out of 5.
- **Example**:

```javascript
axios.post('https://flavourfinder.tjthouhid.com/reviews.php', {
    reviewer_name: 'Tj Thouhid',
    reviewer_email: 'tjthouhid@gmail.com',
    comment: 'Review Text',
    star_rating: '5'
}, {
    params: {
        api_key: 'your_api_key',
        restaurant_id: 'restaurant_id'
    }
})
.then(response => {
    console.log(response.data);
})
.catch(error => {
    console.error(error);
});
```

- **Response**:

```json
{
    "success": true,
    "message": "Review added successfully"
}
```

### 5. Get All Reviews of restaurent

Retrieve a list of all Reviews by restaurants id in the database.

- **URL**: `/reviews.php`
- **Method**: `GET`
- **Example**:

```javascript
axios.get('https://flavourfinder.tjthouhid.com/restaurent.php', {
    params: {
        api_key: 'your_api_key',
        restaurant_id: 'restaurant_id'
    }
})
.then(response => {
    console.log(response.data);
})
.catch(error => {
    console.error(error);
});
```

- **Response**:

```json
{
    "success": true,
    "reviews": [
        {
            "review_id": 1,
            "restaurant_id": 1,
            "reviewer_name": "Tj Touhid",
            "reviewer_email": "tj@test.com",
            "comment": "Nice Restaurent",
            "star_rating": "3.0"
        },
        {
            "review_id": 2,
            "restaurant_id": 1,
            "reviewer_name": "Tj Touhid",
            "reviewer_email": "tj@test.com",
            "comment": "Nice Restaurent",
            "star_rating": "4.0"
        },
        {
            "review_id": 3,
            "restaurant_id": 1,
            "reviewer_name": "Tj Touhid",
            "reviewer_email": "tj2@test.com",
            "comment": "Nice Restaurent",
            "star_rating": "5.0"
        }
    ]
}
```


## Error Handling

If an error occurs, the API will return an error response with an appropriate status code and message.
