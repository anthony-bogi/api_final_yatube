# Проект «API для Yatube»

### Описание:

Yatube - это социальная сеть, где любой пользователь может найти любую интересующую его информацию. Понравилась запись? Пожалуйста, заходи в группу и читай ещё больше постов на заданную тему? Увидел в авторе родную душу? Заходи на его страничку - там ещё больше его авторских работ! Хочешь ещё большего или возникло желание поделиться своими собственными мыслями - регистрируйся. Только зарегистрированным пользователям доступно создание собственных постов, подписка на других авторов и возможность комментировать записи. Однако даже не думай менять или удалять чужие записи - ничего не выйдет, на это имеет право лишь автор поста.

В данном проекте представлен API для взаимодействия с Yatube с помощью обмена JSON сообщениями.

### Установка:

Клонировать репозиторий и перейти в него в командной строке:

```
git clone https://github.com/anthony-bogi/api_final_yatube.git
```

```
cd yatube_api
```

Cоздать и активировать виртуальное окружение (используйте команды "py" или "python"):

```
py -3.7 -m venv venv
```

```
source venv/Scripts/activate
```

Установить зависимости из файла requirements.txt:

```
py -m pip install --upgrade pip
```

```
pip install -r requirements.txt
```

Выполнить миграции:

```
cd yatube_api
```

```
py manage.py migrate
```

Запустить проект:

```
py manage.py runserver
```

Теперь в браузере или в программе для взаимодействия с API (например, Postman), можете перейти по адресу http://127.0.0.1:8000/api/v1/ для запросов к API проекта.

### Примеры:

Получение публикаций.

Получить список всех публикаций:
```
GET http://127.0.0.1:8000/api/v1/posts/
```

Создать публикацию:
```
POST http://127.0.0.1:8000/api/v1/posts/
```
Пример POST-запроса:
```
{
  "text": "Текст публикации",
  "image": "Изображение-string",
  "group": 0
}
```

Получение публикации по известному id:
```
GET http://127.0.0.1:8000/api/v1/posts/{id}/
```

Обновление публикации по известному id:
```
PUT http://127.0.0.1:8000/api/v1/posts/{id}/
```
Пример PUT-запроса:
```
{
  "text": "Текст публикации",
  "image": "Изображение-string",
  "group": 0
}
```

Обновление конкретных полей публикации по известному id:
```
PATCH http://127.0.0.1:8000/api/v1/posts/{id}/
```
Пример запроса:
```
{
  "text": "Текст публикации",
  "group": 0
}
```

Удаление публикации по известному id:
```
DELETE http://127.0.0.1:8000/api/v1/posts/{id}/
```

Получение и добавление комментариев к посту по известному id.

Получение всех комментариев к посту по изветсному id:
```
GET http://127.0.0.1:8000/api/v1/posts/{post_id}/comments/
```

Добавление комментария к посту по известному id:
```
POST http://127.0.0.1:8000/api/v1/posts/{post_id}/comments/
```
Пример запроса:
```
{
  "text": "Текст комментария"
}
```

Получение комментария к посту по известным id поста и автора:
```
GET http://127.0.0.1:8000/api/v1/posts/{post_id}/comments/{id}/
```

Обновление комментария по известным id поста и автора:
```
PUT http://127.0.0.1:8000/api/v1/posts/{post_id}/comments/{id}/
```
Пример запроса:
```
{
  "text": "Текст комментария"
}
```

Частичное обновление комментария по известным id поста и автора:
```
PATCH http://127.0.0.1:8000/api/v1/posts/{post_id}/comments/{id}/
```
Пример запроса:
```
{
  "text": "Текст комментария"
}
```

Удаление комментария по известным id поста и автора:
```
DELETE http://127.0.0.1:8000/api/v1/posts/{post_id}/comments/{id}/
```

Получение списка сообществ:
```
GET http://127.0.0.1:8000/api/v1/groups/
```

Получение информации о сообществе по его id:
```
GET http://127.0.0.1:8000/api/v1/groups/{id}/
```

Подписки.

Возвращает все подписки пользователя, сделавшего запрос. Анонимные запросы запрещены.
```
GET http://127.0.0.1:8000/api/v1/follow/
```

Подписка пользователя, от имени которого сделан запрос, на пользователя, переданного в теле запроса. Анонимные запросы запрещены.
```
POST http://127.0.0.1:8000/api/v1/follow/
```
Пример запроса:
```
{
  "following": "пользователь"
}
```

Работа с JWT-токенами.

Получить JWT-токен:
```
POST http://127.0.0.1:8000/api/v1/jwt/create/
```
Пример запроса:
```
{
  "username": "имя",
  "password": "пароль"
}
```

Обновить JWT-токен:
```
POST http://127.0.0.1:8000/api/v1/jwt/refresh/
```
Пример запроса:
```
{
  "refresh": "refresh"
}
```

Проверить JWT-токен:
```
POST http://127.0.0.1:8000/api/v1/jwt/verify/
```
Пример запроса:
```
{
  "token": "token"
}
```
