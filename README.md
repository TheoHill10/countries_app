# Country API

## Overview

A Country API that allows you to add, remove and view countries.

## Getting Started

### Prerequisites

- Node.js
- npm
- A cloud-based database hosting platform, such as [Superbase](https://supabase.com/)

#### Installation

1. Clone the repository
    - Run `git clone github_url` in the CLI of your choice
2. Navigate to the project directory
    - Navigate using `cd country_api`
3. Install dependencies
    - Run `npm install` to install all dependencies
    - This project uses:
        - Express
        - pg
        - cors
        - dotenv
        - nodemon for development
4. Setup your database
    - Create a database on Supabase, or other clour-based database management systems platform.
    - Retreive the database URL and copy it
    - Create a `.env` file in the root directory with the following:
        - `DB_URL=<your_database_url>`
    - Replace `<your_database_url>` with URL you just copied from Supabase
    - Run `npm run setup-db` to setup the database
5. Setup your port
    - Add a `PORT` key assigned to the port of your choice in your `.env` file
        - `PORT=<port_of_your_choice>`
6. Run the server
    - Run `npm run dev` to run the server in development mode
    - Run `npm run start` to run the server in production mode

### Database Schema
This database was created with postgreSQL<br>
`country` - table name
```sql
country_id: Integer, Primary Key
name: String, not null
capital: String, not null
population: Integer, not null
languages: String, not null
fun_fact: String, not null
map_image_url: String, not null
```
## API Endpoints

All available API endpoints with their methods and descriptions

### Base URL
`http://localhost:<port>/countries` (or your deployed URL)

### API Endpoints
| Method | Endpoint                  | Description                  |
|--------|---------------------------|------------------------------|
| GET    | /countries                | Retrieves all countries      |
| GET    | /countries/:name          | Retrieves a single country   |
| POST   | /countries                | Creates a new country        |
| PATCH  | /countries/:name          | Updates a countries info     |
| DELETE | /countries/:name          | Deletes a country            |

## Get all countries 
### Example Request
To retreive all countries, you can use the following `GET` request: <br>
`GET /countries` <br>
`curl -X GET http://localhost:<port>/countries`

### Example Response
A successful response will return a JSON array of countries object, similar to the following: 
```json
[
    {
    "id": 1,
    "name": "country1",
    "capital": "capital1",
    "population": 1,
    "languages": "language1",
    "fun_fact": "fact1",
    "map_image_url": "url1"
    },
    {
    "id": 2,
    "name": "country2",
    "capital": "capital2",
    "population": 2,
    "languages": "language2",
    "fun_fact": "fact2",
    "map_image_url": "url2"
    },
]
```

## Retreive a single country

### Example Request
To retreive just one country, you can use the following `GET` request: <br>
`GET /countries/:` <br>
`curl -X GET http://localhost:<port>/countries/:name`

### Example Response
A successful response will return a single JSON array of the countries object, similar to the following: 
```json
{
    "id": 1,
    "name": "country1",
    "capital": "capital1",
    "population": 1,
    "languages": "language1",
    "fun_fact": "fact1",
    "map_image_url": "url1"
}
```

## Create a new county

### Example Request
To create a new country, you can use the following `POST` request: <br>
`POST /countries/` <br>
`curl -X POST http://localhost:<port>/countries/`

### Example input
For creation of a new country you will only need to add the name, capital, population and languages to the body. An example format is:
```json
{
    "name": "country1",
    "capital": "capital1",
    "population": 1,
    "languages": "language1",
}
```

## Updating a countries information

### Example Request
To update a countries information, you can use the following `PATCH` request: <br>
`PATCH /countries/:name` <br>
`curl -X PATCH http://localhost:<port>/countries/:name`

### Example input
For updating a countries information you can only update the name, capitl, populationa and language by changing the information in the body in the same format as: 
```json
{
    "name": "country1",
    "capital": "capital1",
    "population": 1,
    "languages": "language1",
}
```

## Deleting a countries infomation

### Example Request
To delete a countries information, you can use the following `DELETE` request: <br>
`DELETE /countries/:name` <br>
`curl -X DELETE http://localhost:<port>/countries/:name`