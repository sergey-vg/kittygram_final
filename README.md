# 🐱 Kittygram

![CI](https://github.com/sergey-vg/kittygram_final/actions/workflows/main.yml/badge.svg)

**Kittygram** — это веб-приложение, в котором пользователи могут делиться анкетами и фотографиями своих котиков, редактировать информацию о них, ставить "лайки" и просматривать карточки других котов. Проект ориентирован на учебную и демонстрационную цель, реализован с продакшн-окружением и CI/CD.

**Демо-версия доступна по адресу:**  
[https://kittygramserg.zapto.org/(https://kittygramserg.zapto.org/)

---

## Описание: обычная vs продакшн-версия

- **Обычная (локальная)** версия предназначена для разработки, запускается через `runserver` и использует SQLite или локальную PostgreSQL.
- **Продакшн-версия** запускается в контейнерах Docker, включает сервер WSGI Gunicorn, Nginx, PostgreSQL, защиту через переменные окружения, сборку статики, и подходит для деплоя на удалённый сервер.

Используйте локальную версию для разработки и тестирования, а продакшн — для публикации и демонстрации.

---

## ⚙️ Технологии проекта

- **Бэкенд**: Python 3.9, Django, Gunicorn
- **Фронтенд**: React, Node.js
- **База данных**: PostgreSQL
- **CI/CD**: GitHub Actions
- **Контейнеризация**: Docker, Docker Compose
- **Веб-сервер**: Nginx
- **Оповещения**: Telegram bot (по завершению деплоя)

---

## Развёртывание проекта

### Локальный запуск

1. Склонируйте репозиторий:

```bash
git clone https://github.com/sergey-vg/kittygram_final.git
cd kittygram_final
```

2. Создайте файл `.env` в корне, на основе примера: файл '.env.example'.

3. Соберите и запустите контейнеры:

```bash
docker compose -f docker-compose.yml up -d --build
```

4. Примените миграции и соберите статику:

```bash
docker compose -f docker-compose.yml exec backend python manage.py migrate
docker compose -f docker-compose.yml exec backend python manage.py collectstatic --noinput
```

5. Приложение будет доступно по адресу: `http://localhost`

---

## CI/CD

GitHub Actions автоматически собирает и развёртывает проект при пуше в ветку main. Весь деплой настраивается через `docker-compose`, образы хранятся в Docker Hub, а уведомления отправляются в Telegram.

### Настройки:

1. Добавьте перменные в Secrets проекта
```
DOCKER_PASSWORD - пароль от Docker Hub
DOCKER_USERNAME - имя пользователя Docker Hub
HOST - ip сервера
SSH_KEY - ключ ssh для доступа к удаленному серверу
SSH_PASSPHRASE - пароль ssh
TELEGRAM_TO - id пользователя TELEGRAM
TELEGRAM_TOKEN - TELEGRAM токен
USER - имя пользователя сервера
```
2. Создайте файл `.env` в корне проекта на сервере, на основе примера: файл '.env.example'.

## 👤 Автор

Сергей В.  
Python-разработчик  
[GitHub: sergey-vg](https://github.com/sergey-vg)