# Run Docker

## Start and Stop Docker Server

```
docker-compose up
docker-compose down
```

## Run Django Test

```
docker-compose run --rm app sh -c "python main.py test"
```

## Run Django Server

```
docker-compose run --rm app sh -c "python main.py runserver"
```

## Make Django Migrations and Migrate

```
docker-compose run --rm app sh -c "python main.py makemigrations"
docker-compose run --rm app sh -c "python main.py migrate"
```