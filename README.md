### ✅ Project: CineSeek – API Documentation Overview

## API Overview

The **MoviesDatabase API** is a comprehensive RESTful API for discovering movies and TV shows. It provides access to a wide variety of movie data including titles, genres, release years, plot summaries, and poster images. It supports filtering and searching, making it ideal for building movie discovery applications.

## Version

**API Version:** v1

## Available Endpoints

* **`/titles`**: Fetch a list of movie and TV show titles with optional filters (genre, year, etc.).
* **`/titles/search/title`**: Search for movies or shows by title name.
* **`/titles/x/titles-by-ids`**: Retrieve multiple titles by their unique IDs.
* **`/titles/random`**: Fetch a random movie or TV show title.
* **`/titles/x/upcoming`**: Get a list of upcoming movie releases.
* **`/titles/x/genres`**: Fetch available genres used in the database.
* **`/titles/x/popular`**: Retrieve currently trending or popular titles.

## Request and Response Format

### Sample Request

```http
GET /titles
Headers:
  x-rapidapi-key: YOUR_API_KEY
  x-rapidapi-host: moviesdatabase.p.rapidapi.com
```

### Sample Response

```json
{
  "entries": 50,
  "results": [
    {
      "id": "tt1234567",
      "titleText": { "text": "Inception" },
      "releaseYear": { "year": 2010 },
      "primaryImage": { "url": "https://image.url" },
      "plot": { "plotText": { "plainText": "A thief who steals corporate secrets..." } }
    }
  ]
}
```

## Authentication

All requests require an API key provided in the headers.

* `x-rapidapi-key`: Your personal API key (keep it secret)
* `x-rapidapi-host`: Must always be `moviesdatabase.p.rapidapi.com`

These headers authenticate and authorize your requests to access data from the MoviesDatabase API.

## Error Handling

Common HTTP error codes returned:

* **401 Unauthorized**: Invalid or missing API key
* **403 Forbidden**: Access to the resource is denied
* **404 Not Found**: The requested endpoint/resource could not be found
* **429 Too Many Requests**: Rate limit exceeded
* **500 Internal Server Error**: An unexpected error occurred on the server

Handle errors using `try/catch` blocks and always check for `response.ok` before parsing data.

## Usage Limits and Best Practices

* **Rate Limits**: The API has a limit on the number of requests per day/minute. Exceeding this returns a 429 error.
* **Efficient Requests**: Use pagination (`limit`, `page`) to load data in chunks instead of all at once.
* **Caching**: Cache repeated or popular requests to reduce load.
* **API Key Security**: Store your API key in `.env.local` and never expose it in frontend code.

