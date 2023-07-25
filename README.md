# Steps to install and run Carnot project:

**\* Using linux terminal**

## Clone the github repo in you PC

1.  ```
        git clone [ssh/http]@githubrepo
    ```

## Setting up virtual enviroment

1. Make virtual venv

```
    python -m venv carnot_venv
```

2. Install requirement

   1. Install requirements with requirements.txt file

   ```
       pip install -r carnot_project/requirements.txt
   ```

   2. If requirements.txt file is not install due to some dependency error install following libraries

   ```
       pip install django
       pip install redis
       pip install psycopg2
       pip install psycopg2-binary
       pip install djangorestframework
   ```

## Setup Postgres on you pc

1. sudo apt update
2. sudo apt install postgresql postgresql-contrib
3. sudo systemctl start postgresql.service

4. sudo su postgres
5. psql
6. Create user and database
   ```
       CREATE USER carnot WITH ENCRYPTED PASSWORD '123';
       CREATE DATABASE carnot;
       GRANT ALL PRIVILEGES ON DATABASE carnot TO carnot;
       GRANT ALL PRIVILEGES ON ALL TABLES IN SCHEMA public TO carnot;
       GRANT ALL PRIVILEGES ON ALL SEQUENCES IN SCHEMA public TO carnot;
       GRANT ALL PRIVILEGES ON ALL FUNCTIONS IN SCHEMA public to carnot;
       Check if things are working corretly using `psql -h localhost -U carnot -W carnot` from shell
   ```

## Install Redis on your pc

1. Steps:

   ```
       sudo apt install redis-server
       sudo nano /etc/redis/redis.conf
       # change the "supervised no" to "supervised systemd"
       sudo systemctl restart redis.service
       sudo systemctl status redis

   ```

## Migrate your Django models in your database:

1.  ```
        python manage.py makemigrations
        python manage.py migrate
        python manage.py runserver
    ```

## Ingestion data to database:

1.

```
    python manage.py ingestion
```

## Now go to localhost:8000/api/ and there you can check the API's.
