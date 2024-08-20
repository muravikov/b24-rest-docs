# Удаление связанных сущностей

{% note warning "Мы еще обновляем эту страницу" %}

Тут может не хватать некоторых данных — дополним в ближайшее время

{% endnote %}

{% if build == 'dev' %}

{% note alert "TO-DO _не выгружается на prod_" %}

- нужны правки под стандарт написания
- не указаны типы параметров
- не указана обязательность параметров
- отсутствуют примеры
- отсутствует ответ в случае успеха
- отсутствует ответ в случае ошибки

{% endnote %}

{% endif %}

{% note info "landing.landing.removeEntities" %}

**Scope**: [`landing`](../../../scopes/permissions.md) | **Кто может выполнять метод**: `любой пользователь`

{% endnote %}

Метод `landing.landing.removeEntities` удаляет связанные сущности лендинга - блоки, и картинки блоков.

{% note warning %}

При удалении блоков связанные с ними картинки удаляются в любом случае. Но может возникнуть ситуация, когда для очистки мусора, необходимо удалить картинки независимо от блока. Используйте данный метод в этом случае.

{% endnote %}

## Параметры

#|
|| **Параметры** | **Описание** | **С версии** ||
|| **lid**
[`unknown`](../../../data-types.md) | Идентификатор лендинга. ||
|| **data**
[`unknown`](../../../data-types.md) | Ассоциативный массив, где в ключе **blocks** содержатся блоки на удаление, а в ключе **images** пары блок-картинка, в которых требуется удалить изображения (блоки в таком случае не удаляются). ||
|#

## Пример

```js
BX24.callMethod(
    'landing.landing.removeEntities',
    {
        lid: 648,
        data: {
            blocks: [12167, 123],
            images: [
                {
                    block: 12269,
                    image: 6866
                },
                {
                    block: 12268,
                    image: 6861
                }
            ]
        }
    },
    function(result)
    {
        if(result.error())
        {
            console.error(result.error());
        }
        else
        {
            console.info(result.data());
        }
    }
);
// В примере мы удаляем блоки с ID 12167, 123, а также картинку 6866 (из блока 12269) и картинку 6861 (из блока 12268).
// Все сущности лежат в лендинге 648.
```

{% include [Сноска о примерах](../../../../_includes/examples.md) %}