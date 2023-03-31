---
description: Информация о маршруте API /api/v1/users
---

# Users

## Объект User

```json
{
    "nickname": "string",
    "rank": "number",
    "permissions": "number",
    "city": "number"
}
```

## Получение пользователей

{% swagger method="get" path="/" baseUrl="/api/v1/users" summary="Список всех пользователей" %}
{% swagger-description %}
Возвращает список объектов User. Если доступ есть ко всем городам, то возвращаются пользователи всех городов, в ином случае только для города, в котором имеется доступ.
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" required="true" %}
Токен доступа
{% endswagger-parameter %}

{% swagger-response status="401: Unauthorized" description="Токен недействительный" %}

{% endswagger-response %}

{% swagger-response status="403: Forbidden" description="У вас нет прав на редактирование" %}

{% endswagger-response %}

{% swagger-response status="200: OK" description="ОК" %}
```json
{
    "code": 0,
    "users": []
}
```


{% endswagger-response %}
{% endswagger %}

{% swagger method="get" path="/:id" baseUrl="/api/v1/users" summary="Информация о пользователе" %}
{% swagger-description %}
Получить информацию о пользователе
{% endswagger-description %}

{% swagger-parameter in="path" required="true" %}
UUID пользователя
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" required="true" %}
Токен доступа
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Успех!" %}
```json
{
    "code": 0,
    "user": {}
}
```


{% endswagger-response %}

{% swagger-response status="401: Unauthorized" description="Токен недействителен" %}

{% endswagger-response %}

{% swagger-response status="403: Forbidden" description="Нет прав или пользователь не найден" %}

{% endswagger-response %}
{% endswagger %}
