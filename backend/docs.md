
# API Documentation

This document describes all REST API endpoints provided by this service.

## Math API
### 1. Circle
**Endpoint:** `GET /math/circle/:radius`  
**Description:** Calculates the area and circumference of a circle.  
**Response Type:** JSON  
**Example Request:**  
`/math/circle/2`

**Example Response:**
{
  "area": 12.566370614359172,
  "circumference": 12.566370614359172
}

### 2. Rectangle

**Endpoint:** `GET /math/rectangle/:width/:height`
**Description:** Calculates the area and perimeter of a rectangle.
**Response Type:** JSON
**Example Request:**
`/math/rectangle/4/2`

**Example Response:**
{
  "area": 8,
  "perimeter": 12
}
### 3. Power (with optional square root)

**Endpoint:** `GET /math/power/:base/:exponent`
**Description:** Computes `base` raised to `exponent`. Optional query parameter `root=true` also returns the square root of the base.
**Response Type:** JSON

**Example Request:**
`/math/power/4/2`

**Example Response:**
{
  "result": 16
}

**Example Request With Root:**
`/math/power/9/2?root=true`

**Example Response With Root:**
{
  "result": 81,
  "root": 3
}
## QuoteBook API
### Categories Used
* successQuotes
* perseveranceQuotes
* happinessQuotes

### 1. Fetch Categories

**Endpoint:** `GET /quotebook/categories`
**Description:** Returns all quote categories as plain text.
Each line begins with `"A possible category is "`.

**Example Response:**
A possible category is successQuotes
A possible category is perseveranceQuotes
A possible category is happinessQuotes

### 2. Get a Random Quote from a Category

**Endpoint:** `GET /quotebook/quote/:category`
**Description:** Returns a random quote from the specified category.
**Response Type:** JSON

**Example Request:**
`/quotebook/quote/happinessQuotes`

**Example Response:**
{
  "quote": "Happiness is not something ready made. It comes from your own actions.",
  "author": "Dalai Lama"
}

**Invalid Category Response (400):**
{'error': 'no category listed for [category]'}

### 3. Add a Quote

**Endpoint:** `POST /quotebook/quote/new`
**Description:** Adds a new quote to the specified category.
**Required Body Fields:** `category`, `quote`, `author`

**Example Request Body:**
{
  "category": "successQuotes",
  "quote": "Your new quote here.",
  "author": "Anonymous"
}

**Success Response (plain text):**
Success!

**Error Response (400):**
{ "error": "invalid or insufficient user input" }

## Server Port
const PORT = process.env.PORT || 8000;


