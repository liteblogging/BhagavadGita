# Bhagavad Gita

<img src="app/static/images/app/gita.png" width="500">

[![Build Status](https://travis-ci.org/gita/BhagavadGita.svg?branch=master)](https://travis-ci.org/gita/BhagavadGita) ![Python](https://camo.githubusercontent.com/c589348df8bb82948f724198f52725d3d36ce738/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f707974686f6e2d332e782d627269676874677265656e2e737667)

Frontend and REST API for BhagavadGita.io

**Backend** - Flask

**Frontend** - Material Design

**Database** - PostgreSQL, ElasticSearch

## REST API

The Bhagavad Gita Application Programming Interface (API) allows a web or mobile developer to use the Bhagavad Gita text in their web or mobile application(s). It follows some of the Best Practices for designing a REST API.

### Current version
The current version of the API is v1. We encourage you to explicitly use this version in the url.

### Schema
All API access is over HTTPS, and accessed from https://bhagavadgita.io/api/v1. All data is sent and received as JSON.

### Authentication
HTTP requests to the BHAGAVAD GITA API are protected with OAUTH2 authentication.
To be able to use the API, you need to be a registered [BhagavadGita.io](https://bhagavadgita.io) user. After signing in, you can register your applications from your Account Dashboard after which you will be issued a Client ID and Client Secret specific to an application that can be used to programatically get the access_token(valid for 300sec).

**How to get an access token?**
Make a POST request to `/auth/oauth/token` with these parameters sent in Headers - 
1. Client ID - Obtained from Account Dashboard after registering an app.
2. Client Secret - Obtained from Account Dashboard after registering an app.
3. Grant Type - Use `client credentials`.
4. Scope - Use `verse` if you just want to access the verses, `chapter` if you just want to access the chapters and `verse chapter` if you want access to both.

Example - 

`curl -X POST "https://bhagavadgita.io/auth/oauth/token" -H "accept: application/json" -H "content-type: application/x-www-form-urlencoded" -d "client_id=YOUR_CLIENT_ID&client_secret=YOUR_CLIENT_SECRET&grant_type=client_credentials&scope=verse%20chapter"`

Then, you can use the received access_token to access any of the endpoints. You can send the access_token as a header or as a query parameter.

Examples -

1. Query Parameter

`curl -X GET "https://bhagavadgita.io/v1/chapters?access_token=YOUR_ACCESS_TOKEN" -H "accept: application/json"`

2. Header

`curl -X GET \
  https://bhagavadgita.io/v1/chapters \
  -H 'Authorization: Bearer YOUR_ACCESS_TOKEN'`

### Documentation

We have 2 types of documenatations available for this API, both based on the Open API specification.
1. [Swagger UI](https://bhagavadgita.io/apidocs/)
2. [ReDoc](https://bhagavadgita.io/docs/)

## Developing Locally

1. Fork this repository and clone the forked repository.
2. Create and activate a Python 3 virtualenv.
3. Use `pip install -r requirements.txt` to install the requirements.
4. `python manage.py runserver` to start the server.
5. Create an environment file `config.env`. Please open an issue or email contact@bhagavadgita.io for the credentials of the file.
6. Frontend can be accessed at `http://127.0.0.1:5000` and API docs can be accessed at `http://127.0.0.1:5000/apidocs/`.

## Contributing

Bug reports and pull requests are welcome on GitHub at https://github.com/gita/BhagavadGita. This project is intended to be a safe, welcoming space for collaboration, and contributors are expected to adhere to the [Contributor Covenant](http://contributor-covenant.org) code of conduct.

To submit a pull request -

1. Fork/clone the repository.
2. Develop.
3. Create a new branch from the master branch.
4. Open a pull request on Github describing what was fixed or added.
