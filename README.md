
# Identity and Access Management

## Coffee Shop

This project is a completed web based coffee shop menu app that enables customers to view avaialable beverages including ingredients. The application has features that enable the store manager to manage all beverages in the cafe.

The application supports the following functionalities:

1. Display drinks both in summarized form and detail form
2. Delete drinks.
3. Add drinks.
4. Edit drinks.
## Setting up the Backend

### Install Dependencies

1. **Python 3.7** - Follow instructions to install the latest version of python for your platform in the [python docs](https://docs.python.org/3/using/unix.html#getting-and-installing-the-latest-version-of-python)

2. **Virtual Environment** - We recommend working within a virtual environment whenever using Python for projects. Instructions for setting up a virual environment for your platform can be found in the [python docs](https://packaging.python.org/guides/installing-using-pip-and-virtual-environments/)

3. **PIP Dependencies** - Once your virtual environment is setup and running, install the required dependencies by navigating to the `/backend` directory and running:

```bash
pip install -r requirements.txt
```

#### Key Pip Dependencies

- [Flask](http://flask.pocoo.org/) is a lightweight backend microservices framework. Flask is required to handle requests and responses.

- [SQLAlchemy](https://www.sqlalchemy.org/) is the Python SQL toolkit and ORM we'll use to handle the lightweight sqlite database.

- [Flask-CORS](https://flask-cors.readthedocs.io/en/latest/#) is the extension we'll use to handle cross-origin requests from our frontend server.

### AUTH0 security keys
This backend requires auth0 api keys to autheticate and authorise users. In order for this to work create a .env file in the `./src` directory with your following auth0 keys.

```
AUTH0_DOMAIN='your_auth0_domain'
API_AUDIENCE='your_api_audience_key'
```
### Run the Server

From within the `./src` directory first ensure you are working using your created virtual environment.

To run the server, execute:

```
flask run --reload
```

## Testing

This project includes a postman collection with test cases that can be used to test all the API endpoints.

## API Reference

### Getting Started
- Base URL: The backend app is hosted at the default, `http://127.0.0.1:5000/`. 
- Authentication: This application requires Auth0 authentication token for barista and manager user roles. 

### Error Handling
Errors are returned as JSON objects in the following format:
```
{
    "success": False, 
    "error": 400,
    "message": "bad request"
}
```
The API will return four error types when requests fail:
- 400: Bad Request
- 404: Resource Not Found
- 422: Not Processable
- 403: Permission not found

### Endpoints 
#### GET /drinks
- General:
    - Fetches a list of all drinks in short form representation
- Request Arguments: None

#### GET /drinks-detail:
    - Fetches a list of all drinks in detail form representation, this includes drink ingredients
- Request Arguments: Auth0 Bearer token

#### DELETE /drinks/{drink_id}
- General:
    - Delete a drink using a drink ID.
- Request Arguments: Auth0 Bearer token, drink_id (int) mandatory

#### POST /drinks 
- General:
    - Create a drink.
- Request Arguments:Auth0 Bearer token, title ( string) mandatory, ingredients list (object array) mandatory

#### PATCH /drinks/{drink_id} 
- General:
    - Update a drink.
- Request Arguments:Auth0 Bearer token, title ( string) mandatory, ingredients list (object array) mandatory
