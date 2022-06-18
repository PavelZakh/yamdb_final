![example workflow](https://github.com/PavelZakh/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)

## Проект yamdb

С помощью этого API вы сможете оставлять отзывы с оценками на различные произведения. А также комментировать эти отзывы. Для этого необходимо зарегестрироватьсяв нашем api.

Развернутый проект доступен по ссылке http://178.154.197.159/api/v1/auth/signup/

### Как развернуть проект локально:

Для начала необходимо установить Docker.
```
https://docs.docker.com/engine/install/
```
Клонировать репозиторий и перейти в него в командной строке:
```
git clone https://github.com/PavelZakh/yamdb_final.git
```
Перейти в папку infra
```
cd infra
```
Выполнить команду по запуску контейнеров
```
docker compose up
```
Готово! Теперь у вас запущен проект!

### Примеры запросов к API:

Регистрация:
```
POST http://localhost/api/v1/auth/signup/
```
Запрос:
```
{
    "email": "email@mail.ru",
    "username": "new_user"
}
```
Ответ:
```
{
    "email": "email@mail.ru",
    "username": "new_user"
}
```
После этого на почту придет код подтверждения, который необходимо использовать для аунтификации на нашем сервисе
```
POST http://localhost/api/v1/auth/token/
```
Запрос:
```
{
    "username": "new_user",
    "confirmation_code": "сode_from_email"
}
```
Ответ:
```
{
  "token": "string"
}
```
После успешной авторизации вы получить Bearer Token, Который необходимо добалять в header любого запроса.
Теперь можно оставлять рейтинг и давать ревью для произведений

Получить список доступных жанров:
```
GET http://localhost/api/v1/genres/
```
Ответ:
```
[
  {
    "count": 0,
    "next": "string",
    "previous": "string",
    "results": [
      {
        "name": "string",
        "slug": "string"
      }
    ]
  }
]
```
Получить список доступных произведений:
```
GET http://localhost/api/v1/titles/
```
Ответ:
```
[
  {
    "count": 0,
    "next": "string",
    "previous": "string",
    "results": [
      {
        "id": 0,
        "name": "string",
        "year": 0,
        "rating": 0,
        "description": "string",
        "genre": [
          {}
        ],
        "category": {
          "name": "string",
          "slug": "string"
        }
       }
    ]
  }
]
```
Оставить отзыв:
```
POST http://localhost/api/v1/follow/
```
```
{
  "text": "string",
  "score": 5
}
```
Ответ:
```
{
  "id": 0,
  "text": "string",
  "author": "string",
  "score": 1,
  "pub_date": "2019-08-24T14:15:22Z"
}
```
Получить полную документацию со всеми запросами можно запустив сервер и перейти по ссылке: 
```
http://localhost/redoc/
```

### Об авторе

Захаров Павел Валерьевич
Студент Яндекс.Практикума по python backend разработке
Telegram - https://t.me/zkhrv_pash