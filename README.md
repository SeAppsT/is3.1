# is3.1

#### Закрытый проект



### POST /auth

 **Авторизация существующего пользователя**

#### Request:

```
{"login": "seapps", "password": "password"}
```

#### Response:

```
{
    "token": "eyJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJzZWFwcHMiLCJyb2xlcyI6WyJST0xFX1VTRVIiXSwiaWF0IjoxNTgzMjU0Mzc2LCJleHAiOjE1ODMzNDA3NzZ9.iRJE9cr1Bx7pRxijAHkOUnOXEPPkq7tTpQzU5fOG3Bc",
    "user": {
        "id": 4,
        "login": "seapps",
        "password": "$2y$12$NotBY8PO6DjU/NB4Y7qFKOI2xqG46RYNnDUycEEmx4V3kTg0TfVGy",
        "status": "ACTIVE"
    }
}
```

### POST /entity

**Добавить запись**

### PUT /entity

**Обновить записи**

### DELETE /entity

**Удалить записи**

**Для этих запросов одинаковое тело:**

```
{
    "id": <int> | может быть пустым,
    "table": <string>, не может быть пустым
    "get": [
        <массив строк>, только для select
    ],
    "change": {
        <string>: <object>, изменяемые поля
    },
    "conditions": {
        <string>: <object>, поля-условия
    },
    "utils": {
        <string>: <object>, утилиты запроса
    }
}
```

### POST /entity/table

**Возвращает массив данных и массив описания полей**

#### Examples:

#### Request:

```
{
    "table": "products",
    "list_id": 7,
    "get": [
    	"price",
    	"description",
    	"name"
    ],
    "conditions": {
        "name": "Phone"
    }
}
```

#### Response:

```
{
    "data": [
        {
            "price": 50000,
            "description": "Cool laptop for freelancers",
            "name": "Phone"
        },
        {
            "price": 20000,
            "description": "Second phone",
            "name": "Phone"
        }
    ],
    "declaration": [
        {
            "id": 4,
            "name": "name",
            "type": "STRING",
            "table_name": "products",
            "title": null,
            "sys": 0,
            "linked_table": null,
            "readonly": 0
        },
        {
            "id": 5,
            "name": "description",
            "type": "STRING",
            "table_name": "products",
            "title": null,
            "sys": 0,
            "linked_table": null,
            "readonly": 0
        },
        {
            "id": 7,
            "name": "price",
            "type": "INT",
            "table_name": "products",
            "title": null,
            "sys": 0,
            "linked_table": null,
            "readonly": 0
        }
    ]
}
```
