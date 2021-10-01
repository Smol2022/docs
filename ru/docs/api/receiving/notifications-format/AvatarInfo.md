# Аватар контакта

Входящее уведомление данного типа содержит данные об аватаре контакта по запрошенному номеру телефона

## Уведомление {#webhook}

### Формат уведомления {#webhook-parameters}

Параметр | Тип | Описание
----- | ----- | -----
`typeWebhook` | **string** | [Тип входящего уведомления](type-webhook.md). Для уведомлений данного типа поле принимает значение `deviceInfo`
`instanceData` | **object** | Данные об аккаунте
`timestamp` | **integer** | Время наступления события в UNIX-формате
`deviceData` | **object** | Данные об устройстве

Поля объекта `instanceData`

Параметр | Тип | Описание
----- | ----- | -----
`idInstance` | **integer** | Идентификатор аккаунта
`wid` | **string** | Идентификатор аккаунта в формате WhatsApp
`typeInstance` | **string** | Тип мессенджера для аккаунта

Поля объекта `avatarInfo`

Параметр | Тип |  Описание
----- | ----- | ----- 
`chatId` | **boolean** | Идентификатор чата, для которого получен аватар контакта
`existsWhatsapp` | **boolean** | Флаг наличия учетной записи WhatsApp на номере телефона корреспондента
`urlAvatar` | **string** | Ссылка на аватар корреспондента или группового чата. Параметр принимает пустое значение в случае, если аватар не установлен или у корреспондента нет учетной записи WhatsApp (`existsWhatsapp`=`false`)
`reason` | **string** | Причина почему аватар не был проверен. Присутствует когда не удалось выполнить проверку, возможные значения:
| | `bad request data` - Неверный формат номера телефона. Номер телефона должен содержать 11 или 12 цифр. Или идентификатора чата
| | `get avatar timeout limit exceeded` - Превышен лимит времени ожидания ответа о наличии аватара

### Пример тела уведомления {#webhook-example-body}

```json
{
    "typeWebhook": "deviceInfo",
    "instanceData": {
        "idInstance": 1234,
        "wid": "79001234567@c.us",
        "typeInstance": "whatsapp"
    },
    "timestamp": 1586700802,
    "avatarInfo": {
        "chatId": "79001234560@c.us",
        "existsWhatsapp": true,
        "urlAvatar": "https://pps.whatsapp.net/v/t61.24694-24/180589560_n.jpg?ccb=11-4&oh=f3fb1&oe=615A60EB"
    },
}
```