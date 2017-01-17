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
            "level": 1,
            "group_name": "Коробка передач",
            "id": 10338,
            "parent_id": null,
            "child_exist": true,
            "items": [
              {
                "type": "CARS_FOREIGN",
                "level": 2,
                "group_name": "Автоматическая коробка передач",
                "id": 10340,
                "parent_id": 10338,
                "child_exist": true,
                "items": [
                  {
                    "type": "CARS_FOREIGN",
                    "level": 3,
                    "group_name": "Масла",
                    "id": 11915,
                    "parent_id": 10340,
                    "child_exist": false,
                    "items": []
                  }
                ]
              },
              {
                "type": "CARS_FOREIGN",
                "level": 2,
                "group_name": "Ступенчатая коробка передач",
                "id": 10339,
                "parent_id": 10338,
                "child_exist": true,
                "items": [
                  {
                    "type": "CARS_FOREIGN",
                    "level": 3,
                    "group_name": "Масла",
                    "id": 12093,
                    "parent_id": 10339,
                    "child_exist": false,
                    "items": []
                  }
                ]
              }
            ]
        },{
            "type": "CARS_FOREIGN",
            "level": 1,
            "group_name": "Система охлаждения",
            "id": 10107,
            "parent_id": null,
            "child_exist": true,
            "items": [
              {
                "type": "CARS_FOREIGN",
                "level": 2,
                "group_name": "антифриз",
                "id": 12305,
                "parent_id": 10107,
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

### Значения countries

| Имя точка | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| type | string | - | Тип кузова |
| mark | string | - | Название каталога (всегда будет AFTERMARKET) |
| mark_short_name | string | - | Сокращенное название марки |
| model_id | integer | - | Идентифкационный номер модели |
| model_name_eng | string | - | Название модели на английском |
| modification_id | integer | Да | Идентифкационный номер модификации |
| name | string | - | Название модификации |
| modification_type | string | - | Тип модификации |

### Значения breadcrumbs

| Имя точка | Тип | Описание |
| :---- | :------: | :--------------- |
| name | string | Имя хлебной крошки |
| url | string | Адрес текущей хлебной крошки |


## `GET /:type//:mark/:mark_short_name/:model_id/:modification_id/:group_id`

Для перехода к списку номеров нужно выбрать группу и передать ее идентификатор (id) в GET параметры