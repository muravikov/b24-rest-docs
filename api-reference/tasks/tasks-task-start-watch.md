# Включение наблюдения за задачей

{% if build == 'dev' %}

{% note alert "TO-DO _не выгружается на prod_" %}

- не указаны типы параметров
- не указана обязательность параметров
- отсутствуют примеры (должно быть три примера - curl, js, php)
- отсутствует ответ в случае ошибки
- отсутствует ответ в случае успеха
 
{% endnote %}

{% endif %}

{% note warning "Мы еще обновляем эту страницу" %}

Тут может не хватать некоторых данных — дополним в ближайшее время

{% endnote %}

{% note info "tasks.task.startwatch" %}

**Scope**: [`task`](../scopes/permissions.md) | **Кто может выполнять метод**: `любой пользователь`

{% endnote %}

Метод `tasks.task.startwatch` позволяет наблюдать за задачей.

#|
|| **Параметр** / **Тип** | **Описание** ||
|| **taskId**
[`unknown`](../data-types.md) | Идентификатор задачи. ||
|#

## Пример

```js
BX24.callMethod(
    'tasks.task.startwatch',
    {taskId:1},
    function(res){console.log(res.answer.result);}
);
```

{% include [Сноска о примерах](../../_includes/examples.md) %}