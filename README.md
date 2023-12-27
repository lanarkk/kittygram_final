![Kittygram workflow](https://github.com/lanarkk/kittygram_final/actions/workflows/main.yml/badge.svg)
![Static Badge](https://img.shields.io/badge/%D0%B1%D1%8D%D0%BA%D0%B5%D0%BD%D0%B4-django-blue)
![Static Badge](https://img.shields.io/badge/framework-django%20rest%20framework-blue)
![Static Badge](https://img.shields.io/badge/%D0%90%D1%83%D1%82%D0%B5%D0%BD%D1%82%D0%B8%D1%84%D0%B8%D0%BA%D0%B0%D1%86%D0%B8%D1%8F-JWT%2Bdjoser-blue)
[![Generic badge](https://img.shields.io/badge/Деплой-docker-blue.svg)](https://shields.io/)
# kittygram_final
## Описани проекта:

Проект kittygram_final - это социальная сеть, в которой пользователи делятся котиками. Коту можно добавить фотографию и достижения, обязательно нужно указать имя и возраст, выбрать цвет. Своих котов можно редактировать и удалять, на чужих же просто смотреть и восхищаться!

## Как запустить проект:

Клонировать репозиторий и перейти в него в командной строке:
Установить docker и docker compose:

### Для Windows 10 и 11: ставим Windows Subsystem for Linux

Установите Windows Subsystem for Linux по [инструкции](https://learn.microsoft.com/ru-ru/windows/wsl/install) с официального сайта Microsoft.

### После установки WSL: установка Docker на Windows

Зайдите на [официальный сайт проекта](https://www.docker.com/products/docker-desktop/) и скачайте установочный файл Docker Desktop.

После установки и перезапуска компьютера Docker Desktop готов к работе! Зелёная полоска с китом в левом нижнем углу окна приложения означает, что докер-демон успешно запустился.

### Установка Docker на Linux

Скачайте и установите curl:

```
sudo apt update
sudo apt install curl
```

Скачайте скрипт для установки докера с официального сайта:

```
curl -fSL https://get.docker.com -o get-docker.sh
```

Запустите сохранённый скрипт:

```
sudo sh ./get-docker.sh
```

Установите утилиту Docker Compose:

```
sudo apt install docker-compose-plugin
```

Проверьте, что Docker работает:

```
sudo systemctl status docker
```

### Установка Docker на macOS

Зайдите на [официальный сайт проекта](https://www.docker.com/products/docker-desktop/) и скачайте установочный файл Docker Desktop для вашей платформы:

Откройте скачанный DMG-файл и перетащите Docker в Applications, а потом — запустите программу Docker.

Проверить работоспособность docker и docker-compose:

```
docker -v
docker-compose -v
```

### Запуск проекта

Клонируйте репозиторий и перейдите в него командами:

```
git clone https://github.com/yandex-praktikum/kittygram_final.git
```

```
cd kittygram_final
```

Создаем файл .env:

```
touch .env
```

Заполняем .env согласно примеру в .env.example: 

```
PRACTICUM_SECRET_KEY=your_secret_key
POSTGRES_USER=kittygram_user
POSTGRES_PASSWORD=kittygram_password
POSTGRES_DB=kittygram
DB_HOST=db
DB_PORT=5432
```

Пока docker работает запустите docker-compose, соберите статику и примените миграции командой:

```
docker compose -f docker-compose.production.yml up -d 
docker compose -f docker-compose.production.yml exec backend python manage.py migrate
docker compose -f docker-compose.production.yml exec backend python manage.py collectstatic
docker compose -f docker-compose.production.yml exec backend cp -r //app/collected_static/. //backend_static/static/
```

Для Linux:

```
sudo docker compose -f docker-compose.production.yml -d
sudo docker compose -f docker-compose.production.yml exec backend python manage.py migrate
sudo docker compose -f docker-compose.production.yml exec backend python manage.py collectstatic
sudo docker compose -f docker-compose.production.yml exec backend cp -r /app/collected_static/. /backend_static/static/
```

## Автор:

Федякин Максим.

Ссылки: [github](https://github.com/lanarkk), [telegram](https://t.me/rapedwhore).