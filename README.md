# API для Yatube

### ![Я](https://yastatic.net/q/logoaas/v2/Яндекс.svg?circle=black&color=000&first=white)![Практикум](https://yastatic.net/q/logoaas/v2/Практикум.svg?color=000)

### **Стек**
![python version](https://img.shields.io/badge/Python-3.10-green)
![django version](https://img.shields.io/badge/Django-3.2-green)
![django_rest_framework version](https://img.shields.io/badge/DjangoRestFramework-3.12-green)
![djoser version](https://img.shields.io/badge/Djoser-2.2-green)

## Описание
В проекте реализован REST API для Yatube, который позволяет получать 
информацию о постах, комментариях, группах и авторах, а так же 
создавать и редактировать свои записи и комментарии, подписываться
на новых авторов, и просматривать список подписок.

# Установка
## Как запустить проект:

Клонировать репозиторий и перейти в него в командной строке:

```
git clone https://github.com/iNTENSY/api_final_yatube.git
```

```
cd api_yatube
```

Cоздать и активировать виртуальное окружение:

```
python -m venv venv
```

```
venv/Scripts/activate
```

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

## Примеры запросов
### Получение списка публикаций
Для получения списка всех публикаций необходимо отправить 
Get-запрос на адрес `http://127.0.0.1:8000/api/v1/posts/`.
При помощи параметров `limit` и `offset` можно настроить размер
и область выдачи

Пример ответа:
```
[
    {
        "id": 1,
        "author": "a",
        "text": "123123",
        "pub_date": "2023-10-28T08:48:33.711108Z",
        "image": null,
        "group": null
    },
    {
        "id": 2,
        "author": "a",
        "text": "very good text",
        "pub_date": "2023-10-29T08:48:33.711108Z",
        "image": null,
        "group": null
    }
]
```

### Добавление публикации
Для добавления новой публикации необходимо отправить POST-запрос
на адрес `http://127.0.0.1:8000/api/v1/posts/` в JSON формате:

```
{
    "text": "Ваш текст",
    "group": 1
} 
```
Пример ответа:
```
    {
        "id": 3,
        "author": "a",
        "text": "Ваш текст",
        "pub_date": "2023-10-29T08:48:33.711108Z",
        "image": null,
        "group": 1
    }
```
### Добавление комментария
Для добавления новой публикации необходимо отправить POST-запрос
на адрес `http://127.0.0.1:8000/api/v1/posts/4/comments/` в JSON формате:
```
{
    "text": "текст комментария"
} 
```
Пример ответа:
```
{
    "id": 1,
    "author": "a",
    "post": 1,
    "text": "текст комментария",
    "created": "2023-10-29T08:48:33.711108Z"
} 
```
### Добавление подписки
Для добавления новой подписки необходимо отправить POST-запрос
на адрес `http://127.0.0.1:8000/api/v1/follow/` в JSON формате с именем автора, 
на которого хотите подписаться:
```
{
    "following": "name"
} 
```
Пример ответа:
```
{
    "id": 1,
    "user": "a",
    "following": "name",
} 
```
Для GET-запроса доступен поиск автора среди подписок.

# Автор
- Даценко Дмитрий
