# Flask JWT Protection API

Це API, створене на Flask, яке використовує JWT (JSON Web Token) для захисту доступу до ресурсів. Користувачі можуть отримати токен після успішної авторизації, який необхідно використовувати для доступу до захищених маршрутів.

## Основні функції

- Генерація JWT токенів із терміном дії на 30 днів.
- Захист маршрутів за допомогою JWT.
- Авторизація через облікові дані "admin" та "adminpassword".
- Збереження даних у базі SQLite.

## Інструкція з установки

1. Клонуйте репозиторій:
    ```bash
    git clone https://your-repository-url.git
    ```

2. Перейдіть у папку з проєктом:
    ```bash
    cd JWT-Protection
    ```

3. Встановіть залежності:
    ```bash
    pip install -r requirements.txt
    ```

4. Ініціалізуйте та налаштуйте базу даних:
    ```bash
    flask db init
    flask db migrate
    flask db upgrade
    ```

## Запуск

1. Запустіть сервер:
    ```bash
    python run.py
    ```

2. API готове до використання.

## Опис API

### 1. Авторизація та отримання токена

**Метод**: `POST`  
**Ресурс**: `/login`

**Приклад запиту**:
```json
{
    "username": "admin",
    "password": "adminpassword"
}
```

**Приклад відповіді**:
```json
{
    "access_token": "your-jwt-token"
}
```

### 2. Отримання списку елементів

**Метод**: `GET`  
**Ресурс**: `/item`

**Приклад відповіді**:
```json
[
    {
        "id": 1,
        "name": "Item 1",
        "description": "Description of item 1",
        "price": 19.99
    }
]
```

### 3. Отримання елемента за ID

**Метод**: `GET`  
**Ресурс**: `/item/<item_id>`

**Приклад відповіді**:
```json
{
    "id": 1,
    "name": "Item 1",
    "description": "Description of item 1",
    "price": 19.99
}
```

### 4. Додавання нового елемента

**Метод**: `POST`  
**Ресурс**: `/item`

**Приклад запиту**:
```json
{
    "name": "Item 2",
    "description": "Description of item 2",
    "price": 29.99
}
```

**Приклад відповіді**:
```json
{
    "id": 2,
    "name": "Item 2",
    "description": "Description of item 2",
    "price": 29.99
}
```

## Типові помилки

- **401 Unauthorized**: Відсутній або недійсний токен.
- **403 Forbidden**: Прострочений токен.
- **404 Not Found**: Елемент не знайдено.

#### Розробив: Кириченко Кіріл  
#### Група: I-23  
