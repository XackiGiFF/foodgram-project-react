# Foodgram

![workflow](https://github.com/Xewus/Foodgram/actions/workflows/main.yml/badge.svg)

***
Господа, раз уж скачиваете (собственно, для этого оно и открыто) справа вверху можно тыкнуть :star: .  
:warning: В `docker-compose.yml` в настройках для `nginx` вам нужно будет сменить порт :eight::zero::zero::one: на :eight::zero:.

У меня так настроено, потому что на одном сервере и IP висит несколько сайтов.
***

## Tecnhologies:
- Python 3.10
- Django 4.0
- Django REST framework 3.13
- Nginx
- Docker
- Postgres


## http://213.189.221.245


Here you can share recipes of dishes, add them to favorites and display a shopping list for cooking your favorite dishes.
To preserve order - only administrators are allowed to create tags and ingredients.

### To deploy this project need the next actions:
- Download project with SSH (actually you only need the folder 'infra/')
```
git@github.com:Xewus/foodgram-project-react.git
```
- Connect to your server:
```
ssh <server user>@<server IP>
```
- Install Docker on your server
```
sudo apt install docker.io
```
- Install Docker Compose (for Linux)
```
sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
```
- Get permissions for docker-compose
```
sudo chmod +x /usr/local/bin/docker-compose
```
- Create project directory (preferably in your home directory)
```
mkdir foodgram && cd foodgram/
```
- Create env-file:
```
touch .env
```
- Fill in the env-file like it:
```
DEBUG=False
SECRET_KEY=<Your_some_long_string>
ALLOWED_HOSTS='localhost, 127.0.0.1, <Your_host>'
CSRF_TRUSTED_ORIGINS='http://localhost, http://127.0.0.1, http://<Your_host>'
DB_ENGINE='django.db.backends.postgresql'
DB_NAME='postgres'
POSTGRES_USER='postgres'
POSTGRES_PASSWORD=<Your_password>
DB_HOST='db'
DB_PORT=5432
```
- Copy files from 'infra/' (on your local machine) to your server:
```
scp -r infra/* <server user>@<server IP>:/home/<server user>/foodgram/
```
- Run docker-compose
```
sudo docker-compose up -d
```
Wait a few seconds...
Your service is work!
![Иллюстрация к проекту](https://github.com/Xewus/Foodgram/blob/master/screen.png)

## Enjoy your meal !

# Commands

For first deploy create static on server
```bash
docker exec -it foodgram_backend_1 python manage.py collectstatic --noinput
```

Migrations:
```bash
docker exec -it foodgram_backend_1 python manage.py migrate --noinput
```

Makemigrations:
```bash
docker exec -it foodgram_backend_1 python manage.py makemigrations --noinput
```

Load ingredients ( data/ingredients.csv ):
```bash
docker exec -it foodgram_backend_1 python manage.py load_ingrs
```

Load tags ( data/tags.csv ):
```bash
docker exec -it foodgram_backend_1 python manage.py load_tags
```

For make superuser Django - 
```bash
docker exec -it foodgram_backend_1 python manage.py createsuperuser
```

### *Backend by:*
[Xewus](https://github.com/Xewus)

