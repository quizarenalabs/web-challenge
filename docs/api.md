# <img height="80" src="images/qa-web-challenge-header.png" alt="qa-web-challenge-server" />

## Usage

The API is available at https://api.web-challenge.infra.quizarena.com/{version} (example for v1: https://api.web-challenge.infra.quizarena.com/v1/players/1).

## API v1

All routes are public and do not require any authentication. All responses are in JSON.

### GET /players/:id

Return the profile of a Player

```json
{
  "id": 5,
  "first_name": "Cynthia",
  "last_name": "Sipes",
  "company": "Hickle Group",
  "city_name": "Leesburg",
  "last_seen": "2024-01-24T10:12:20.054Z",
  "picture": "https://avatars.githubusercontent.com/u/61174386",
  "total_events": 198,
  "total_friends": 111
}
```

### GET /players/:id/friends

Return the list of friends of for a Player.

```json
[
  {
    "id": 222,
    "first_name": "Leonard",
    "last_name": "Littel",
    "company": "Treutel, O'Keefe and Rippin",
    "city_name": "Lake Chelsiefield",
    "last_seen": "2023-05-24T14:28:06.252Z",
    "picture": "https://avatars.githubusercontent.com/u/36128789",
    "total_events": 112,
    "total_friends": 263
  },
  {
    "id": 55,
    "first_name": "Yvette",
    "last_name": "Wolff-Kub",
    "company": "Flatley Group",
    "city_name": "Mitchelboro",
    "last_seen": "2023-08-17T15:26:06.994Z",
    "picture": "https://avatars.githubusercontent.com/u/86263038",
    "total_events": 156,
    "total_friends": 46
  },
  ...
]
```

### GET /players/:id/upcoming-events

Return the upcoming events for a Player.

```json
[
  {
    "id": 50,
    "name": "Golf",
    "date": "2024-02-28T06:02:56.225Z",
    "participants": [
      {
        "id": 1163501204668416,
        "first_name": "Henrietta",
        "last_name": "Reinger",
        "company": "Bechtelar - Dibbert",
        "city_name": "Kingstead",
        "last_seen": "2023-11-18T08:45:50.531Z",
        "picture": "https://avatars.githubusercontent.com/u/47977304",
        "total_events": 223,
        "total_friends": 232
      },
      ...
    ]
  },
  ...
]

```

## API v2

Routes are the same as v1, but now require a `x-token` (in lowercase) header with a valid token.

To get a valid token, you must call the `/login` endpoint.

To call the `/login` endpoint, you must use a valid username and password. You can use any username as long as the password is equal to the username.

### POST /login

Authenticate a user with a password and return a token.

Request body:

```json
{
  "username": "user",
  "password": "password"
}
```

Response:

```json
{
  "token": "xxxx"
}
```
