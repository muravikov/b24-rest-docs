# Обзор методов

Каждый **смарт-процесс** — это новая сущность в рамках CRM, для которой создается новый раздел со своим интерфейсом, набором функционала, полями, элементами и т.д. Подробнее можно прочитать в [документации](https://dev.1c-bitrix.ru/api_d7/bitrix/crm/dynamic/index.php).

Порядок работы со смарт-процессом следующий:

1. Создается новый смарт-процесс [crm.type.add](crm-type-add.md).
2. При создании смарт-процесса независимо от настроек будет создано направление по умолчанию. При желании его можно [изменить/добавить](#воронки-смарт-процессов).
3. При создании направления независимо от настроек к нему создается набор стадий по умолчанию. При желании их можно [изменить/удалить](#стадии-смарт-процессов).
4. Создаются пользовательские поля для этого смарт-процесса. [Подробнее](../user-defined-fields/index.md)
5. Можно работать с его [элементами](#элементы-смарт-процессов).
6. Можно вынести смарт-процесс в Цифровое рабочее место. [Подробнее](../../automated-solution/index.md)
7. Можно настроить как личную, так и общую карточку элементов смарт-процессов. [Подробнее](#управление-настройками-карточки-элемента-смарт-процесса)
8. Есть возможность дополнить функциональность за счет событий.


## Методы работы со смарт-процессами

- [{#T}](./crm-type-fields.md) 
- [{#T}](./crm-type-add.md)
- [{#T}](./crm-type-update.md)
- [{#T}](./crm-type-get.md)
- [{#T}](./crm-type-list.md)
- [{#T}](./crm-type-delete.md)


## Элементы смарт-процессов

Методы работы с элементами смарт-процессов описаны в отдельном [разделе](../index.md)

### Методы работы с элементами смарт-процессов

- [{#T}](../crm-item-fields.md)
- [{#T}](../crm-item-add.md)
- [{#T}](../crm-item-update.md)
- [{#T}](../crm-item-get.md)
- [{#T}](../crm-item-list.md)
- [{#T}](../crm-item-delete.md)


## Воронки смарт-процессов

Для работы с воронками смарт-процессов необходим обязательный параметр `entityTypeId`, который можно получить посредством методов [`crm.type.add`](crm-type-add.md) или [`crm.type.list`](crm-type-list.md)

### Направления по умолчанию

У каждого типа сущности одновременно может быть только одно направление по умолчанию. В связи с этим есть ряд ограничений:

- нельзя удалить направление по умолчанию;
- при создании нового направления и передаче ему флага `"isDefault": "Y"` старое направление по умолчанию перестанет быть направлением по умолчанию;
- при изменении направления по умолчанию нельзя сделать его направлением не по умолчанию;
- при изменении направления не по умолчанию с передачей ему флага `"isDefault": "Y"` старое направление по умолчанию перестанет быть направлением по умолчанию.

Если для имеющегося смарт-процесса отключен показ направлений в интерфейсе, то работа с направлениями через rest всё равно возможна.

### Методы работы с воронками

- [{#T}](../category/crm-category-fields.md)
- [{#T}](../category/crm-category-add.md)
- [{#T}](../category/crm-category-update.md)
- [{#T}](../category/crm-category-get.md)
- [{#T}](../category/crm-category-list.md)
- [{#T}](../category/crm-category-delete.md)


## Стадии смарт-процессов

### ENTITY_ID

Поле `ENTITY_ID` для стадий смарт-процессов имеет следующий вид: `DYNAMIC_{entityTypeId}_STAGE_{categoryId}`,

где:
- `{entityTypeId}` - идентификатор типа CRM смарт-процесса;
- `{categoryId}` - идентификатор направления, к которому относится стадия.

### STATUS_ID

Поле `STATUS_ID` для стадий смарт-процессов должно иметь префикс `DT{entityTypeId}_{categoryId}`,

где
- `{entityTypeId}` - идентификатор типа CRM смарт-процесса;
- `{categoryId}` - идентификатор направления, к которому относится стадия.

### Пример

`crm.status.add(fields)`

Для создания новой стадии смарт-процесса с `entityTypeId = 135` и `categoryId = 20` параметр `fields` должен иметь следующий вид:

```json
{
    "fields": {
        "COLOR": "#1111AA",
        "NAME": "My new stage",
        "SORT": 250,
        "ENTITY_ID": "DYNAMIC_135_STAGE_20",
        "STATUS_ID": "DT135_20:MY_STAGE_REST"
    }
}
```

### Методы работы со стадиями

- [{#T}](./../../status/crm-status-fields.md)
- [{#T}](./../../status/crm-status-add.md)
- [{#T}](./../../status/crm-status-update.md)
- [{#T}](./../../status/crm-status-get.md)
- [{#T}](./../../status/crm-status-list.md)
- [{#T}](./../../status/crm-status-delete.md)

## Управление настройками карточки элемента смарт-процесса

Методы для управления настройками карточки элемента смарт-процесса предоставляют возможность настраивать отображение и поведение карточек элементов в CRM. Эти методы работают аналогично уже существующим методам для управления настройками карточек сделок, контактов и других сущностей CRM, таким как [`crm.deal.details.configuration.*`](../../deals/custom-form/index.md), [`crm.contact.details.configuration.*`](../../contacts/custom-form/index.md) и так далее.

- [{#T}](../item-details-configuration/crm-item-details-configuration-get.md)
- [{#T}](../item-details-configuration/crm-item-details-configuration-set.md)
- [{#T}](../item-details-configuration/crm-item-details-configuration-reset.md)
- [{#T}](../item-details-configuration/crm-item-details-configuration-forceCommonScopeForAll.md)

## События над смарт-процессами

- [{#T}](../events/type/on-crm-type-add.md)
- [{#T}](../events/type/on-crm-type-update.md)
- [{#T}](../events/type/on-crm-type-delete.md)