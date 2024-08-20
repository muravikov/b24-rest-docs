# Товарные позиции 

## Описание

REST-методы из семейства **crm.item.productrow.\*** позволяют работать с товарными позициями, привязанными к различным объектам CRM. Методы являются универсальными и поддерживают любой тип владельца, который может работать с [новым API CRM](https://dev.1c-bitrix.ru/api_d7/bitrix/crm/crm_new_api.php).

## Права доступа

При обращении к методам REST учитываются права доступа пользователя, от которого осуществляется вызов методов. Товарные позиции не являются самостоятельной сущностью CRM и всегда привязаны к какому-либо объекту CRM, выступающему как их владелец. Поэтому при всех операциях проверяются права пользователя на доступ и управление объектом-владельцем (предложением, смарт-процессом и т.п.). Например, если у пользователя нет доступа к чтению какого-либо элемента, то и прочитать его товарные позиции он не сможет.

## Автоматические действия после любого изменения

После любого изменения, вносимого в товарные позиции, будут выполнены все стандартные проверки и процедуры, происходящие при изменении объекта CRM, в том числе пересчет суммы и запуск роботов после сохранения. Это относится ко всем методам, создающим/изменяющим товарные позиции: [crm.item.productrow.add](./crm-item-productrow-add.md), [crm.item.productrow.update](./crm-item-productrow-update.md), [crm.item.productrow.set](./crm-item-productrow-set.md).

## Обзор методов

> Scope: [`crm`](../../../scopes/permissions.md)
>
> Кто может выполнять методы: в зависимости от метода

#|
|| **Метод** | **Описание** ||
|| [crm.item.productrow.add](./crm-item-productrow-add.md) | Добавляет товарную позицию ||
|| [crm.item.productrow.update](./crm-item-productrow-update.md) | Обновляет товарную позицию ||
|| [crm.item.productrow.get](./crm-item-productrow-get.md) | Получает информацию о товарной позиции по id ||
|| [crm.item.productrow.set](./crm-item-productrow-set.md) | Привязывает товарную позицию к объекту CRM ||
|| [crm.item.productrow.list](./crm-item-productrow-list.md) | Получает список товарных позиций ||
|| [crm.item.productrow.getAvailableForPayment](./crm-item-productrow-get-available-for-payment.md) | Получает список неоплаченных товаров ||
|| [crm.item.productrow.delete](./crm-item-productrow-update.md) | Удаляет товарную позицию ||
|| [crm.item.productrow.fields](./crm-item-productrow-fields.md) | Получает список полей товарных позиций ||
|#