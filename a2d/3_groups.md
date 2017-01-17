# Группы

## `GET /:mark/:category/:model`

Возвращает объект с двумя массивами (groups, breadcrumbs) и объектом model

### Пример запроса

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/CARS_FOREIGN/VAZ/GENERAL/58961
```

### Пример ответа

```json
{
     "model": {
        "type": "CARS_NATIVE",
        "short_name": 58961,
        "name": "X-Ray",
        "name_with_mark": "ВАЗ X-Ray",
        "modification": "Lada XRay",
        "mark_short_name": "VAZ",
        "category": "GENERAL",
        "years": null,
        "index": 896,
        "relevance": null,
        "image": "58961.jpg"
    },
    "groups": [
        {
            "name": "Принадлежности",
            "childs": [
                {
                    "name": "Инструмент и принадлежности",
                    "childs": [
                        {
                            "short_name": 3373769,
                            "name": "Инструмент"
                        }
                    ]
                }
            ]
        }
        ...
    ],
    "breadcrumbs": [
        ...
        {
            "name": "X-Ray",
            "url": "58961"
        }
    ]
}
```

### Значения model

| Имя | Тип | Описание |
| :---- | :------: | :--------------- |
| type | string | Тип транспортного средства |
| short_name | integer | Наименование модели |
| name | string | Наименование модели |
| name_with_mark | string | Наименование модели с указанием марки |
| modification | string | Модификация |
| mark_short_name | string | Идентификатор марки |
| category | string | Тип каталога |
| years | string |  |
| index | integer | Порядковый номер |
| relevance | string (date) | Применяемость |
| image | string | URL изображения |

### Значения groups

| Имя | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| name | string | - | Наименование основной группы |
| childs | array | - | Группы |
| childs[..].name | string | - | Наименование группы |
| childs[..].childs | array | - | Подгруппы |
| childs[..].childs[..].short_name | integer | Да | Идентификатор подгруппы |
| childs[..].childs[..].name | string | - | Наименование подгруппы |

### Значения breadcrumbs

| Имя | Тип | Описание |
| :---- | :------: | :--------------- |
| name | string | Имя хлебной крошки |
| url | string | адрес текущей хлебной крошки |


## `GET /:mark/:category/:model/:short_name`

Для перехода к списку модификаций нужно выбрать модель и передать ее идентификатор (short_name) в GET параметры