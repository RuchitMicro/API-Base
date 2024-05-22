
# APIBase Class Documentation

## Overview

This `APIBase` class is designed to facilitate API interactions with a configurable and extensible approach. It uses `axios` for making HTTP requests and `sweetalert2` for handling alert messages. The class provides methods for performing GET, POST, PUT, PATCH, and DELETE requests, along with utilities for token management, request debouncing, and error handling.

## Table of Contents

1. [Constructor](#constructor)
2. [Methods](#methods)
    - [addToken](#addtoken)
    - [handleRequestInterception](#handlerequestinterception)
    - [handleSuccessResponse](#handlesuccessresponse)
    - [extract_error_message](#extract_error_message)
    - [handleErrorResponse](#handleerrorresponse)
    - [makeRequest](#makerequest)
    - [get](#get)
    - [post](#post)
    - [put](#put)
    - [patch](#patch)
    - [delete](#delete)
    - [getToken](#gettoken)
    - [setToken](#settoken)
    - [removeToken](#removetoken)
    - [formatDate](#formatdate)
    - [parseJSON](#parsejson)
    - [serializeParams](#serializeparams)
    - [checkStatus](#checkstatus)
    - [extractErrorMessage](#extracterrormessage)
    - [buildAuthHeader](#buildauthheader)
    - [logRequest](#logrequest)
    - [debounceRequest](#debouncerequest)
    - [validateResponseSchema](#validateresponseschema)
    - [tokenRefreshInterceptor](#tokenrefreshinterceptor)
3. [Configuration](#configuration)
4. [Usage](#usage)

## Constructor

### `constructor(config)`

Initializes the `APIBase` instance with the provided configuration.

#### Parameters:

- `config`: Object containing configuration options:
    - `baseURL` (required): Base URL for API requests.
    - `defaultHeaders`: Default headers for all requests (optional).
    - `timeout`: Request timeout in milliseconds (optional).
    - `tokenKey`: Key for storing JWT token in local storage (optional).
    - `retryLimit`: Number of retries for failed requests (optional).
    - `debounceDelay`: Delay for debouncing requests (optional).

## Methods

### `addToken(token)`

Adds the provided token to the request headers.

### `handleRequestInterception(config)`

Handles request interception logic, e.g., adding auth tokens.

### `handleSuccessResponse(response)`

Handles successful responses.

### `extract_error_message(data)`

Extracts error messages from response data.

### `handleErrorResponse(error)`

Handles error responses and displays appropriate alerts using `sweetalert2`.

### `makeRequest(method, endpoint, data, headers, params)`

Makes an API request using the specified method, endpoint, data, headers, and parameters.

### `get(endpoint, params, headers)`

Performs a GET request to the specified endpoint with optional parameters and headers.

### `post(endpoint, data, headers)`

Performs a POST request to the specified endpoint with the provided data and headers.

### `put(endpoint, data, headers)`

Performs a PUT request to the specified endpoint with the provided data and headers.

### `patch(endpoint, data, headers)`

Performs a PATCH request to the specified endpoint with the provided data and headers.

### `delete(endpoint, headers)`

Performs a DELETE request to the specified endpoint with the provided headers.

### `getToken()`

Retrieves the JWT token from local storage.

### `setToken(token)`

Stores the provided token in local storage.

### `removeToken()`

Removes the token from local storage.

### `formatDate(date)`

Formats a date into a human-readable string.

### `parseJSON(response)`

Safely parses a JSON response.

### `serializeParams(params)`

Serializes URL parameters.

### `checkStatus(response)`

Checks if the response status is successful.

### `extractErrorMessage(error)`

Extracts error messages from responses.

### `buildAuthHeader(token)`

Builds the Authorization header with the provided token.

### `logRequest(url, method, data)`

Logs the request details.

### `debounceRequest(func)`

Debounces a function to prevent rapid firing of requests.

### `validateResponseSchema(response, schema)`

Validates the response schema.

### `tokenRefreshInterceptor(apiClient, refreshToken)`

Interceptor for handling token refresh logic.

## Configuration

The `APIBase` class can be configured with the following options:

- `baseURL`: Base URL for API requests (required).
- `defaultHeaders`: Default headers for all requests (optional).
- `timeout`: Request timeout in milliseconds (optional, default: 30000).
- `tokenKey`: Key for storing JWT token in local storage (optional).
- `retryLimit`: Number of retries for failed requests (optional, default: 1).
- `debounceDelay`: Delay for debouncing requests (optional).

## Usage

```javascript
import APIBase from "./APIBase";

const api = new APIBase({
    baseURL: "https://api.example.com",
    defaultHeaders: {
        "Content-Type": "application/json",
    },
    timeout: 30000,
    tokenKey: "access_token",
    retryLimit: 3,
    debounceDelay: 200,
});

// Example usage
api.get("/endpoint")
   .then(response => console.log(response))
   .catch(error => console.error(error));
```

