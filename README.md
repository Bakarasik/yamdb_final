# REST API YaMDB
![DjangoREST](https://img.shields.io/badge/DJANGO-REST-ff1709?style=for-the-badge&logo=django&logoColor=white&color=ff1709&labelColor=gray) ![Docker](https://img.shields.io/badge/docker-%230db7ed.svg?style=for-the-badge&logo=docker&logoColor=white) ![Nginx](https://img.shields.io/badge/nginx-%23009639.svg?style=for-the-badge&logo=nginx&logoColor=white)
![Django-app workflow](https://github.com/Bakarasik/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)
### Описание:
API для базы данных с отзывами на фильмы, музыку, сериалы и другие прозведения. 
Учебный проект, создан командой учеников Яндекс.Практикумы.

### Техническое описание проекта:
На странице с документацией localhost/redoc/ можно ознакомиться с примерами запросов и ответов на них.

### Зависимости:
Python 3.8  
Django 2.2  
Django rest framework 3.12

## Примеры API-запросов:

#### Получение списка всех произведений

```http
  GET /api/v1/titles/
```

| Parameter | Type     | Description                |
| :-------- | :------- | :------------------------- |
| `token`   | `string` | **Required**. Ваш токен    |

#### Добавление нового отзыва к произведению

```http
  POST /api/v1/titles/{id}/reviews/
```

| Parameter | Type     | Description                       |
| :-------- | :------- | :-------------------------------- |
| `token`   | `string` | **Required**. Ваш токен           |
| `id`      | `string` | **Required**. Id произведения     |
| `text`    | `string` | **Required**. Текст отзыва        |
| `score`   | `integer` | **Required**. Оценка произведения |


### Регистрация:
Для регистрации пользователь может самостоятельно отправить свой username и email на /auth/signup/. После этого он получает письмо с кодом подтвержения. Далее необходимо получит токен для аутентификации, использовав код и передав его вместе с username по адресу /auth/token/.

### Запуск проекта в Docker

Создать файл ./api_yamdb/.env c необходимыми переменными
DB_ENGINE=django.db.backends.postgresql 
DB_NAME=postgres 
POSTGRES_USER=postgres 
POSTGRES_PASSWORD=password
DB_HOST=db 
DB_PORT=5432
SECRET_KEY=***

Запустить контейнер
```power shell
  docker-compose up -d --build
```

Применить миграции
```power shell
  docker-compose exec web python manage.py migrate
```

Создать суперюзера
```power shell
  docker-compose exec web python manage.py createsuperuser
```

Собрать статику
```power shell
  docker-compose exec web python manage.py collectstatic --no-input
```

Наполнить базу данных 
```power shell
  docker-compose exec web python manage.py loaddata fixtures.json
```

Посмотреть сайт в работе
```html
  http://yamdb.sytes.net/api/v1/
```

### Авторы: 
- [Екатерина Серова](https://github.com/EISerova/),
- [Анна Бакарасова](https://github.com/Bakarasik),
- [Владимир Мазняк](https://github.com/Cognitoid).