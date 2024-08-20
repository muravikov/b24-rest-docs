# Получение списка разрешений

{% note warning "Мы еще обновляем эту страницу" %}

Тут может не хватать некоторых данных — дополним в ближайшее время

{% endnote %}

{% if build == 'dev' %}

{% note alert "TO-DO _не выгружается на prod_" %}

- отсутствуют параметры или поля
- не указаны типы параметров
- отсутствуют примеры
- отсутствует ответ в случае ошибки

{% endnote %}

{% endif %}

{% note info "scope" %}

**Scope**: [`базовый`](../../scopes/permissions.md) | **Кто может выполнять метод**: `любой пользователь`

{% endnote %}

Если метод `scope` вызван без параметров, то он вернет все разрешения, доступные для данного приложения.

Если же метод вызван с параметром `full=true`, то он вернет полный [список разрешений](https://dev.1c-bitrix.ru/learning/course/index.php?COURSE_ID=99&LESSON_ID=2280).

## Примеры

```http
https://my.bitrix24.ru/rest/scope?auth=d161f25928c3184678924ec127edd29a
```

{% include [Сноска о примерах](../../../_includes/examples.md) %}

## Ответ в случае успеха

> 200 OK
```json
{
    "result":[
        "entity",
        "user",
        "log",
        "department"
    ]
}
```