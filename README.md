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

After installation create the file `~/.pg_service.conf` and insert the following content:

```shell
[local_db]
host=localhost
user=postgres
dbname=django-djacket
port=5432
```

The connection details used are from the docker-compose file.

Furthermore, the file `~/.pgpass` must be created with the following content:

```shell
localhost:*:*:postgres:secret
```

The connection details used are also from the docker-compose file.

### Python requirements

```shell
pip install psycopg2
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