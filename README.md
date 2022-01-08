# Readme

## Project Setup

Please follow the steps below if you want to launch the application for the first time.

### Install Django into virtual environment

```shell
# Set up virtual environment (directory can be freely selected)
python3 -m venv ~/venv/django

# Entering the environment
source ~/venv/django/bin/activate

# Install django
python3 -m pip install django
```

Verify installation with:

```shell
python3 -m django --version
```

### Database requirements

You can start a postgres database container via docker-compose file `docker-compose.yml`.

For python package `psycopg2` you need nevertheless postgres installed on your system. You can do this via:

```shell
brew install postgres
```

### Environment variables

Create file `django-backend/djacket/settings/.env` and insert the following content:

```dotenv
SECRET_KEY={{ django secret key }}
DATASOURCE_DATABASE_NAME=django-djacket
DATASOURCE_HOST=localhost
DATASOURCE_USERNAME=postgres
DATASOURCE_PASSWORD=secret
DATASOURCE_PORT=5432
DEBUG=True
```

The connection details used are from the docker-compose file.
You can create a django secret key via `https://djecrety.ir/`.

### Python requirements

```shell
pip install psycopg2
pip install django-environ
pip install django-rest-framework
pip install django-cors-headers
pip install djoser
pip install pillow
pip install stripe
```

### Create the database model

```shell
python3 manage.py makemigrations
```

This will create migration files within folder `migration` of each app. To run this migration files execute:

```shell
python3 manage.py migrate
```

### Create super user

```shell
python3 manage.py createsuperuser
```

### Start a development server

```shell
python3 manage.py runserver
```