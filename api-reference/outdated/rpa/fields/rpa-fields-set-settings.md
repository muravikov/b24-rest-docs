# Установка полного набора настроек видимости полей на стадии с идентификатором stageId процесса с идентификатором typeId

{% note warning "Мы еще обновляем эту страницу" %}

Тут может не хватать некоторых данных — дополним в ближайшее время

{% endnote %}

{% if build == 'dev' %}

{% note alert "TO-DO _не выгружается на prod_" %}

- отсутствует таблица fields
- отсутствуют примеры
- отсутствует ответ в случае успеха
- отсутствует ответ в случае ошибки

{% endnote %}

{% endif %}

{% note info "rpa.fields.setSettings" %}

**Scope**: [`rpa`](../../../scopes/permissions.md) | **Кто может выполнять метод**: `любой пользователь`

{% endnote %}

Метод `rpa.fields.setSettings` устанавливает полный набор настроек видимости полей на стадии с идентификатором stageId процесса с идентификатором typeId.

#|
|| **Параметр** / **Тип** | **Описание** ||
|| **typeId**^*^ 
[`number`](../../../data-types.md) | Идентификатор процесса. ||
|| **stageId** 
[`number`](../../../data-types.md) | Идентификатор стадии. По умолчанию 0 (общие настройки). ||
|| **fields**^*^ 
[`array`](../../../data-types.md) | Массив с настройками видимости полей. Если передать пустой fields, то все настройки будут стерты. ||
|#

{% include [Сноска о параметрах](../../../../_includes/required.md) %}

## Пример

```json
{
    "typeId": 1,
    "fields": {
        "kanban": [
            "createdBy", 
            "UF_RPA_1_NAME"
        ]
    }
}
```
Метод вернет результат аналогичный запросу  `rpa.fields.getSettings`.

{% include [Сноска о примерах](../../../../_includes/examples.md) %}