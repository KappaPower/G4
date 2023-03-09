# SF_G4_HW
Docker image with Django (nginx, Django, Postgres, Gunicorn)

based on guide django-on-docker
https://testdriven.io/blog/dockerizing-django-with-postgres-gunicorn-and-nginx/

## Dev build
build & run:

```sh
$ docker-compose up -d --build
```

stop:

```sh
$ docker-compose down -v
```

Test it out at http://localhost:8000. The "app" folder is mounted into the container and your code changes apply automatically.


## Prod build
build & run:

```sh
$ docker-compose -f docker-compose.prod.yml up -d --build
$ docker-compose -f docker-compose.prod.yml exec web python manage.py migrate --noinput
$ docker-compose -f docker-compose.prod.yml exec web python manage.py collectstatic --no-input --clear
```

stop:

```sh
$ docker-compose -f docker-compose.prod.yml down -v
```

Test it out at http://localhost:1337. No mounted folders. To apply changes, the image must be re-built.
