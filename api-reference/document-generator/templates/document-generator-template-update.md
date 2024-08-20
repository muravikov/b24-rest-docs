# Изменить шаблон

{% note warning "Мы еще обновляем эту страницу" %}

Тут может не хватать некоторых данных — дополним в ближайшее время

{% endnote %}

{% if build == 'dev' %}

{% note alert "TO-DO _не выгружается на prod_" %}

- не указаны типы параметров
- отсутствуют примеры
- отсутствует ответ в случае ошибки

{% endnote %}

{% endif %}

{% note info "documentgenerator.template.update" %}

**Scope**: [`documentgenerator`](../../scopes/permissions.md) | **Кто может выполнять метод**: `любой пользователь`

{% endnote %}

Метод `documentgenerator.template.update` обновляет существующий шаблон. 

#|
|| **Параметр** | **Описание** ||
|| **id**^*^ | Идентификатор шаблона. ||
|| **fields** | Массив полей. ||
|#

{% include [Сноска о параметрах](../../../_includes/required.md) %}

## Параметры fields

#|
|| **Параметр** | **Описание** ||
|| **name** | Название шаблона. ||
|| **file** | Контент файла, закодированный в `base64` (обязательное). Как альтернативу, контент файла можно передать в `multipart / form-data`. В этом случае его не надо кодировать в `base64`. ||
|| **code** | Символьный код шаблона. ||
|| **numeratorId** | Идентификатор нумератора. ||
|| **region** | Страна. ||
|| **users** | Массив видимости. По умолчанию пусто. ||
|| **active** | Y/N флаг активности. По умолчанию Y. ||
|| **withStamps** | Y/N ставить печати и подписи. По умолчанию N. ||
|| **sort** | Индекс сортировки. ||
|#

Все параметры необязательные.

## Ответ в случае успеха

Возвращает те же данные, что и при вызове [documentgenerator.template.get()](./document-generator-template-get.md).