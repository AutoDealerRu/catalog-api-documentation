# Группы (groups)

## `GET /:type/:mark/:mark_short_name/:model_id/:modification_id`

Возвращает объект с двумя массивам groups и breadcrumbs

| Конечная точка | Описание |
| :---- | :--------------- |
| GET /CARS_FOREIGN/AFTERMARKET/AC/4211/12428 | Группы AC ACE 4.6 |

### Пример запроса

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/CARS_FOREIGN/AFTERMARKET/AC/4211/12428
```

### Пример ответа

```json
{
    "groups": [
        {
            "type": "CARS_FOREIGN",
            "mark": "AFTERMARKET",
            "mark_short_name": "AC",
            "model_id": 4211,
            "modification_id": 12428,
            "level": 1,
            "group_name": "Коробка передач",
            "id": 10338,
            "child_exist": true,
            "items": [
              {
                "id": 10340,
                "level": 2,
                "group_name": "Автоматическая коробка передач",
                "child_exist": true,
                "items": [
                  {
                    "id": 11915,
                    "level": 3,
                    "group_name": "Масла",
                    "child_exist": false,
                    "items": []
                  }
                ]
              },
              {
                "id": 10339,
                "level": 2,
                "group_name": "Ступенчатая коробка передач",
                "child_exist": true,
                "items": [
                  {
                    "id": 12093,
                    "level": 3,
                    "group_name": "Масла",
                    "child_exist": false,
                    "items": []
                  }
                ]
              }
            ]
        },{
            "type": "CARS_FOREIGN",
            "mark": "AFTERMARKET",
            "mark_short_name": "AC",
            "model_id": 4211,
            "modification_id": 12428,
            "level": 1,
            "group_name": "Система охлаждения",
            "id": 10107,
            "child_exist": true,
            "items": [
              {
                "id": 12305,
                "level": 2,
                "group_name": "антифриз",
                "child_exist": false,
                "items": []
              }
            ]
        },
        ...
    ],
    "breadcrumbs": [
        ...
        ,{
            "name": "4.6",
            "url": "12428"
        }
    ]
}
```

### Значения groups

| Имя точка | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| type | string | - | Тип кузова |
| mark | string | - | Название каталога (всегда будет AFTERMARKET) |
| mark_short_name | string | - | Сокращенное название марки |
| model_id | integer | - | Идентифкационный номер модели |
| modification_id | integer | - | Идентифкационный номер модификации |
| id | integer | Да | ID группы |
| level | integer | - | Указатель текущего уровня вложенности (1 ~ 5) |
| group_name | string | - | Имя группы |
| child_exist | boolean | - | Наличие вложенных подгрупп |
| items | array of objects | - | Вложенные группы (если child_exists = false, значит items - пустой) |

### Значения items (вложенность до 4 уровней)

| Имя точка | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| id | integer | Да | ID группы |
| level | integer | - | Указатель текущего уровня вложенности (1 ~ 5) |
| group_name | string | - | Имя группы |
| child_exist | boolean | - | Наличие вложенных подгрупп |
| items | array of objects | - | Вложенные группы (если child_exists = false, значит items - пустой) |

### Значения breadcrumbs

| Имя точка | Тип | Описание |
| :---- | :------: | :--------------- |
| name | string | Имя хлебной крошки |
| url | string | Адрес текущей хлебной крошки |


## `GET /:type/:mark/:mark_short_name/:model_id/:modification_id/:group_id`

### Для перехода к списку номеров нужно выбрать группу и передать ее идентификатор (id) в GET параметры
### ВАЖНО! Ссылкой на следующий уровень оформляется только конечная группа, без вложенных (признак child_exists == false)