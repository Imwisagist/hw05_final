# hw05_final

[![CI](https://github.com/yandex-praktikum/hw05_final/actions/workflows/python-app.yml/badge.svg?branch=master)](https://github.com/yandex-praktikum/hw05_final/actions/workflows/python-app.yml)

Проект YATUBE
Социальная сеть

Описание
Благодаря этому проекту можно создавать посты, оставлять комментарии под постами и подписываться на понравившихся авторов.

Технологии
Python, Django, DRF, DRF-Simple JWT, Django CORS, Pillow, sorl-thumbnail, Bootstrap.

Запуск проекта в dev-режиме
Клонировать репозиторий и перейти в него в командной строке:
Установите и активируйте виртуальное окружение:
Для пользователей Windows:
python -m venv venv
source venv/Scripts/activate
python -m pip install --upgrade pip
Установите зависимости из файла requirements.txt
pip install -r requirements.txt
Перейдите в каталог с файлом manage.py выполните команды: Выполнить миграции:
python manage.py migrate
Создайте супер-пользователя:

python manage.py createsuperuser
Соберите статику:

python manage.py collectstatic
Запуск проекта:

python manage.py runserver
Примеры REST API
По умолчанию для неавторизованных пользователей проект доступен только для чтения.

api/v1/posts/ - все постов,
api/v1/posts/{id}/ - один пост,
api/v1/groups/ - список групп (можно выбрать в качестве темы поста),
api/v1/groups/{id}/ - одна группы,
api/v1/{post_id}/comments/ - все комментарии под определенным постом,
api/v1/{post_id}/comments/{id}/ - конкретный комментарий под определенным постом,
Исключение: follow доступен только авторизованных пользователей.

api/v1/follow/ - получение подписок текущего пользователя
api/v1/follow/{id}/ - получение одной подписки
api/v1/follow/posts/ - получение всех постов избранных авторов
users доступен только для админа:

api/v1/users/ - все пользователи
api/v1/users/{id}/ - один пользователь
Авторизованные пользователи могут создавать посты, комментировать их и подписываться на других пользователей.
Пользователи могут изменять(удалять) контент, автором которого они являются. Так же в проекте присутсвует пагинация(LimitOffsetPagination), поиск и сортировка, примеры ниже
api/v1/posts/?limit=10&offset=0 - Пагинация на 10 постов, начиная с первого
api/v1/posts/?search=your_search - Поиск в тексте, постов пользователя, группы
api/v1/posts/?ordering=-pub_date - сортировка по дате создания постов(сначало новые)
Добавление сообществ проект реализованного через админ панель Django:
admin/admin/ - после авторазиации, перейдите в раздел "сообщества" и создайте тематики
Доступ авторизованным пользователем доступен по jwt-токену, который можно получить выполнив POST запрос по адресу:

api/v1/jwt/create/
Передав в body данные пользователя:

{
"username": "your_nickname",
"password": "your_password"
}
Получив токен его нужно добавить в headers, после этого вам буду доступны все функции проекта:

Authorization: Bearer {your_token}
Проверить и обновить токен можно по следующием эндпоинтам:

api/v1/jwt/refresh/ - Обновление токена
api/v1/jwt/verify/ - Проверка токена
Авторы
Dusky
