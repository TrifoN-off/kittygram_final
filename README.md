# Kittygram

## Описание

Kittygram - это социальная сеть для любителей котиков, построенная на Django REST Framework и React. Проект предоставляет следующие возможности:

- Создание, получение, редактирование и удаление профилей котиков
- Добавление и управление достижениями котиков
- Загрузка и отображение фотографий котиков
- Система аутентификации пользователей
- RESTful API для взаимодействия с данными

## Технологии

### Backend
- **Django 3.2.3** - веб-фреймворк
- **Django REST Framework 3.12.4** - для создания API
- **Djoser 2.1.0** - для аутентификации и управления пользователями
- **PostgreSQL** - база данных
- **Pillow 9.0.0** - для работы с изображениями
- **Gunicorn 20.1.0** - WSGI сервер для продакшена
- **psycopg2-binary 2.9.3** - драйвер PostgreSQL

### DevOps
- **Docker** - контейнеризация
- **Docker Compose** - оркестрация контейнеров
- **Nginx** - веб-сервер
- **GitHub Actions** - CI/CD

## Установка

### Для того, чтобы запустить проект локально необходимо:

1. Клонировать репозиторий и перейти в него в командной строке:
    
    ```bash
    git clone https://github.com/TrifoN-off/kittygram_final.git
    cd kittygram_final
    ```

2. Создать и активировать виртуальное окружение для backend:

    ```
    python3 -m venv env
    ```

    * Если у вас Linux/macOS

        ```
        source env/bin/activate
        ```

    * Если у вас windows

        ```
        source env/scripts/activate
        ```

    ```
    python3 -m pip install --upgrade pip
    ```

3. Установить зависимости backend:

    ```bash
    python3 -m pip install --upgrade pip
    pip install -r requirements.txt
    ```

4. Настроить базу данных PostgreSQL и применить миграции:

    ```bash
    python3 manage.py migrate
    ```

5. Создать суперпользователя (опционально):

    ```bash
    python3 manage.py createsuperuser
    ```

6. Запустить backend сервер:

    ```bash
    python3 manage.py runserver
    ```

7. В новом терминале установить зависимости frontend:

    ```bash
    cd frontend
    npm install
    ```

8. Запустить frontend приложение:

    ```bash
    npm start
    ```

### Для запуска проекта с Docker

1. Клонировать репозиторий:

    ```bash
    git clone https://github.com/TrifoN-off/kittygram_final.git
    cd kittygram_final
    ```

2. Запустить проект с помощью Docker Compose:

    ```bash
    docker-compose up --build
    ```

## Примеры API запросов

### Создание профиля котика

**POST /api/cats/**

**Запрос:**
```json
{
  "name": "Мурзик",
  "color": "black",
  "birth_year": 2020,
  "achievements": [
    {
      "achievement_name": "Лучший охотник"
    }
  ]
}
```

**Ответ:**
```json
{
  "id": 1,
  "name": "Мурзик",
  "color": "black",
  "birth_year": 2020,
  "age": 3,
  "owner": "user123",
  "achievements": [
    {
      "id": 1,
      "achievement_name": "Лучший охотник"
    }
  ],
  "image": null,
  "image_url": null
}
```

### Получение списка котиков

**GET /api/cats/**

**Ответ:**
```json
{
  "count": 1,
  "next": null,
  "previous": null,
  "results": [
    {
      "id": 1,
      "name": "Мурзик",
      "color": "black",
      "birth_year": 2020,
      "age": 3,
      "owner": "user123",
      "achievements": [
        {
          "id": 1,
          "achievement_name": "Лучший охотник"
        }
      ],
      "image": null,
      "image_url": null
    }
  ]
}
```

### Обновление профиля котика

**PATCH /api/cats/{cat_id}/**

**Запрос:**
```json
{
  "name": "Мурзик Обновленный",
  "color": "white"
}
```

### Получение списка достижений

**GET /api/achievements/**

**Ответ:**
```json
[
  {
    "id": 1,
    "achievement_name": "Лучший охотник"
  },
  {
    "id": 2,
    "achievement_name": "Самый пушистый"
  }
]
```

### Создание достижения

**POST /api/achievements/**

**Запрос:**
```json
{
  "achievement_name": "Новое достижение"
}
```


## Автор

**Никита Трифонов**

- GitHub: [TrifoN-off](https://github.com/TrifoN-off)
