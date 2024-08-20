# Добавление универсального дела

{% note warning "Мы еще обновляем эту страницу" %}

Тут может не хватать некоторых данных — дополним в ближайшее время

{% endnote %}

{% if build == 'dev' %}

{% note alert "TO-DO _не выгружается на prod_" %}

- нужны правки под стандарт написания
- не указана обязательность параметров
- отсутствуют примеры
- отсутствует ответ в случае ошибки

{% endnote %}

{% endif %}

{% note info "crm.activity.todo.add" %}

**Scope**: [`crm`](../../../scopes/permissions.md) | **Кто может выполнять метод**: `любой пользователь`

{% endnote %}

Метод `crm.activity.todo.add` добавляет универсальное дело. Результат будет содержать `id` - идентификатор созданного дела.

## Параметры

#|
|| **Параметр** | **Описание** ||
|| **ownerTypeId**
[`number`](../../../data-types.md) | Идентификатор типа элемента (справочник доступных типов), к которому относится дело ||
|| **ownerId**
[`number`](../../../data-types.md) | Идентификатор элемента, к которому относится дело ||
|| **description**
[`string`](../../../data-types.md) | Текст дела ||
|| **deadline**
[`datetime`](../../../data-types.md) | Крайний срок дела ||
|| **responsibleId**
[`number`](../../../data-types.md) | Ответственный за дело ||
|#

## Примеры

```http
crm.activity.todo.add?ownerTypeId=2&ownerId=1&deadline=2022-12-31T15:00:00&description=Связаться с клиентом
```

{% include [Сноска о примерах](../../../../_includes/examples.md) %}

## Ответ в случае успеха

> 200 OK
```json
{
    "result": {
        "id": 243
    }
}
```