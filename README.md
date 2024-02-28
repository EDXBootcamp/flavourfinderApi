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

### 2. Get All Restaurants

Retrieve a list of all restaurants stored in the database.

- **URL**: `/restaurent.php`
- **Method**: `GET`
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


## Error Handling

If an error occurs, the API will return an error response with an appropriate status code and message.
