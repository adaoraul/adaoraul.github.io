---
layout: default
title: Axiom Zen Mastermind Backend Challenge
permalink: mastermind.html
---

# Mastermind Challenge

## API cURL Test
[![asciicast](https://asciinema.org/a/46373.png)](https://asciinema.org/a/46373)

## API Methods

### Authentication

* Endpoint: https://axiomzen-mastermind.herokuapp.com/api/authentication.json
* Method: [POST]

_params:_

```json
{
  "name": "Adão Raul",
  "email": "adao.raul@gmail.com"
}
```

_response:_

```json
{
  "name": "Adão Raul",
  "email": "adao.raul@gmail.com",
  "avatar": "https://secure.gravatar.com/avatar/a89f0cdd5105a822fdd7b5ea17c1c36a.png?r=PG",
  "api_key": "Acyg0rNS5ATBE6AktSUE1wtt"
}
```

----------

### Game

#### List

* Endpoint: https://axiomzen-mastermind.herokuapp.com/api/games.json
* Method: [GET]

_header:_

```
Authorization Token token=$api_key
```

_response:_

```json
{
  "list": [
    {
      "codemaker": {
        "name": "Adão Raul"
      },
      "hashed_id": "356a192b7913b04c54574d18c28d46e6395428ab",
      "played": true
    }
  ]
}
```

----------

#### Create

* Endpoint: https://axiomzen-mastermind.herokuapp.com/api/games.json
* Method: [POST]

_header:_

```
Authorization Token token=$api_key
```

_params:_

```json
{
  "colors": ["R","P","Y","G","O","G","O","P"]
}
```

_response:_

```json
{
  "hashed_id": "356a192b7913b04c54574d18c28d46e6395428ab"
}
```

----------

#### Show
* Endpoint: https://axiomzen-mastermind.herokuapp.com/api/games/:id.json
* Method: [GET]

_header:_

```
Authorization Token token=$api_key
```

_response:_

```json
{
  "status": true,
  "codemaker": {
    "name": "André Souza",
  },
  "codebreaker": {
    "name": "Adão Raul",
  },
  "colors": ["R","P","Y","G","O","G","O","P"],
  "solved": true,
  "time_taken": 64.75358,
  "turns": [
    {
      "guess": ["R","P","Y","G","O","G","O","P"],
      "exact": 3,
      "near": 2
    },
    {
      "guess": ["R","P","Y","G","O","G","O","P"],
      "exact": 2,
      "near": 1
    },
    {
      "guess": ["R","P","Y","G","O","G","O","P"],
      "exact": 3,
      "near": 2
    }
  ]
}
```

----------

#### Play

* Endpoint: https://axiomzen-mastermind.herokuapp.com/games/:game_id/play.json
* Method: [GET]

_header:_

```
Authorization Token token=$api_key
```

_response:_

```json
{
  "hashed_id": "356a192b7913b04c54574d18c28d46e6395428ab",
  "time_left": 299.980998
}
```

----------

#### Guess

* Endpoint: https://axiomzen-mastermind.herokuapp.com/api/games/:game_id/guess.json
* Method: [POST]

_header:_

```
Authorization Token token=$api_key
```

_params:_

```json
{
  "colors": ["R","P","Y","G","O","G","O","P"]
}
```

_response:_

```json
{
  "status": true,
  "exact": 3,
  "near": 2,
  "solved": false,
  "turns": 1,
  "time_limit": 256
}
```

## Running Locally

Make sure you have [Ruby](http://ruby-lang.org/) and the [Heroku Toolbelt](https://toolbelt.heroku.com/) installed.

```sh
$ git clone git@github.com:adaoraul/axiomzen-mastermind.git # or clone your own fork
$ cd axiomzen-mastermind
$ bundle install
$ rake db:create db:migrate
$ foreman start
```

Your app should now be running on [localhost:5000](http://localhost:5000/).

## Deploying to Heroku

```
$ heroku create
$ git push heroku master
$ heroku open
```
or

[![Deploy to Heroku](https://www.herokucdn.com/deploy/button.png)](https://heroku.com/deploy)