# Удаление привязки CRM-сущности (Контакта/Компании) к документу по идентификатору привязки

{% note warning "Мы еще обновляем эту страницу" %}

Тут может не хватать некоторых данных — дополним в ближайшее время

{% endnote %}

{% if build == 'dev' %}

{% note alert "TO-DO _не выгружается на prod_" %}

- не указана обязательность параметров
  
{% endnote %}

{% endif %}

{% note info "catalog.documentcontractor.delete" %}

**Scope**: [`catalog`](../../scopes/permissions.md) | **Кто может выполнять метод**: `любой пользователь`

{% endnote %}

## Описание

```http
catalog.documentcontractor.delete(id)
```

Метод для удаления привязки поставщика к документу.
Если операция успешна, возвращается `true` в теле ответа.

Случаи, когда могут вернуться ошибки:

- если нет доступа к складскому учету, нет доступа на просмотр документов прихода или нет доступа на редактирование документа прихода (добавление/удаление привязки – это редактирование документа);
- не найдена привязка с заданным id.

## Параметры

#|
|| **Параметр** | **Описание** ||
|| **id**
[`integer`](../../data-types.md) | Идентификатор привязки CRM-сущности (Контакта/Компании) к документу. ||
|#

{% include [Сноска о параметрах](../../../_includes/required.md) %}

## Примеры

```js
BX.callMethod(
    'catalog.documentcontractor.delete',
    { id: 20 },
    function(result) {
        if (result.error())
            console.error(result.error().ex);
        else
            console.log(result.data());
    }
);
```

{% include [Сноска о примерах](../../../_includes/examples.md) %}