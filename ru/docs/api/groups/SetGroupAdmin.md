# SetGroupAdmin

Метод назначает участника группового чата администратором.

## Запрос {#request}

Для назначения участника группового чата администратором требуется выполнить запрос по адресу:
```
POST https://api.green-api.com/waInstance{{idInstance}}/SetGroupAdmin/{{apiTokenInstance}}
```

Для получения параметров запроса `idInstance` и `apiTokenInstance` обратитесь к разделу [Перед началом работы](/before-start#parameters).

### Параметры запроса {#request-parameters}

Параметр | Тип | Обязательный | Описание
----- | ----- | ----- | -----
`groupId` | **string** | Да | [Идентификатор группового чата](/api/chat-id#gus)
`participantChatId` | **string** | Да | [Идентификатор](/api/chat-id#corr) участника группы, назначаемого в качестве администратора

### Пример тела запроса {#request-example-body}

Назначение участника группового чата администратором:
```json
{
    "groupId": "79001234567-1587570015@g.us",
    "participantChatId": "79001234568@c.us"
}
```

## Ответ {#response}

### Поля ответа {#response-parameters}

Поле | Тип |  Описание
----- | ----- | ----- 
`setGroupAdmin` | **boolean** | Флаг назначения участника группы администратором

### Пример тела ответа {#response-example-body}

```json
{
    "setGroupAdmin": true
}
```

### Ошибки SetGroupAdmin {#errors}

Перечень общих для всех методов ошибок смотрите в разделе [Стандартные ошибки](/api/common-errors)

## Пример кода на Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/setGroupAdmin/{{apiTokenInstance}}"

payload = "{\r\n    \"groupId\": \"79001234567-1587570015@g.us\",\r\n    \"participantChatId\": \"79001234568@c.us\",\r\n}"
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```