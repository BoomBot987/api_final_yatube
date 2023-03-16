## Проект «API для Yatube» - Яндекс практикум(Спринт 9):
### Описание 

Yatub представляет собой проект социальной сети в которой реализованы  возможности публиковать записи, комментировать записи, а так же подписываться или отписываться от авторов.
В данной версии проекта добавлен API который позоляет пользоваться всеми возможностями проекта.

### Технологии 

* Python 3.11,
* Django 4.2,
* DRF,
* JWT + Djoser

### Запуск проекта

* Клонировать репозиторий и перейти в его корневую папку в командной строке.

```
git@github.com:BoomBot987/api_final_yatube.git
```

```
cd api_final_yatube
```

Cоздать и активировать виртуальное окружение:

```
python -m venv venv
```

```
source venv/Scripts/activate
```

Обновить pip (опционально):

```
python -m pip install --upgrade pip
```

Установить зависимости из файла requirements.txt:

```
pip install -r requirements.txt
```

Выполнить миграции:

```
python manage.py migrate
```

Запустить проект:

```
python manage.py runserver
```

## Примеры работы с API для неавторизованных пользователей

Для неавторизованных пользователей работа с API доступна в режиме чтения.


```r
GET api/v1/posts/ - получить список всех публикаций.
При указании параметров limit и offset выдача будет работать с пагинацией
GET api/v1/posts/{id}/ - получение публикации по id
GET api/v1/groups/ - получение списка доступных сообществ
GET api/v1/groups/{id}/ - получение информации о сообществе по id
GET api/v1/{post_id}/comments/ - получение всех комментариев к публикации
GET api/v1/{post_id}/comments/{id}/ - Получение комментария к публикации по id
```

## Примеры работы с API для авторизованных пользователей

- Для создания публикации используем:

```r
POST /api/v1/posts/
```

в body

```json
{
"text": "string",
"image": "string",
"group": 0
}
```

- Обновление публикации:

```r
PUT /api/v1/posts/{id}/
```

в body

```json
{
"text": "string",
"image": "string",
"group": 0
}
```

- Частичное обновление публикации:

```r
PATCH /api/v1/posts/{id}/
```

в body

```json
{
"text": "string",
"image": "string",
"group": 0
}
```

- Частичное обновление публикации:

```r
DEL /api/v1/posts/{id}/
```

Получение доступа к эндпоинту /api/v1/follow/ (подписки) доступен только для авторизованных пользователей.

подписка пользователя от имени которого сделан запрос на пользователя переданного в теле запроса. Анонимные запросы запрещены.

```r
GET /api/v1/follow/
```

- Авторизованные пользователи могут создавать посты, комментировать их и подписываться на других пользователей.
- Пользователи могут изменять(удалять) контент, автором которого они являются.
- Добавить группу в проект можно только через администратор.

#### Авторизация


Доступ авторизованным пользователем доступен по JWT-токену (Joser), который можно получить выполнив POST запрос по адресу:

```r
POST /api/v1/jwt/create/
```

- Передав в body данные пользователя (например в postman):

```json
{
"username": "string",
"password": "string"
}
```

- Полученный токен добавляем в headers (postman), после чего буду доступны все функции проекта:

```r
Authorization: Bearer {your_token}
```

- Обновить JWT-токен:

```r
POST /api/v1/jwt/refresh/
```

- Проверить JWT-токен:

```r
POST /api/v1/jwt/verify/
```


Автор: 
* [Максим Гребень](https://github.com/BoomBot987)
