# Нажатие пользователя на обычную кнопку

В данном разделе описывается формат входящего уведомления объекта `messageData` для обычных кнопок. Для получения описания общего формата входящих уведомлений обратитесь к разделу [Входящие сообщения](Webhook-IncomingMessageReceived.md). 

## Уведомление {#webhook}

### Формат уведомления {#webhook-parameters}

Поля объекта `messageData`

Параметр | Тип | Описание
----- | ----- | -----
`typeMessage` | **string** | Тип принятого сообщения. Для сообщений данного типа поле принимает значение `buttonsResponseMessage`
`buttonsResponseMessage` | **object** | Объект данных о нажатии пользователя на кнопку

Поля объекта `buttonsResponseMessage`

Параметр | Тип | Описание
----- | ----- | -----
`selectedButtonId` | **string** | идентификатор нажатой кнопки
`selectedButtonText` | **string** | текст нажатой кнопки

### Пример тела уведомления {#webhook-example-body}

```json
{
    "typeWebhook": "incomingMessageReceived",
    "instanceData": {
        "idInstance": 1101000001,
        "wid": "79001234567@c.us",
        "typeInstance": "whatsapp"
    },
    "timestamp": 1656315272,
    "idMessage": "9BB19BB0D568BA7B185EEAD21A33D317",
    "senderData": {
        "chatId": "79001234567@c.us",
        "sender": "79001234567@c.us",
        "senderName": "Green API"
    },
    "messageData": {
        "typeMessage": "buttonsResponseMessage",
        "buttonsResponseMessage": {
            "selectedButtonId": "1",
            "selectedButtonText": "Green"
        }
    }
}
```
