# Номера деталей

## `GET /:mark/:model/:subgroup`

Возвращает объект с двумя массивами (numbers, breadcrumbs) и двумя объектами (model, group)

### Пример запроса

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/CARS_NATIVE/VAZ/58961/3373769
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
        "years": null,
        "index": 896,
        "relevance": null,
        "image": "https://212709.selcdn.ru/autocatalog-online/main/models/58961.jpg"
    },
    "group": {
        "short_name": 3373769,
        "name": "Инструмент",
        "image": "https://acat.online/api/catalogs/CARS_NATIVE/VAZ/GENERAL/58961/3373769/image",
        "coordinates" : [
            {
                "name" : "III",
                "group_short_name" : 26993,
                "coordinate" : {
                    "top" : {
                        "x" : 272,
                        "y" : 67
                    },
                    "bottom" : {
                        "x" : 312,
                        "y" : 97
                    }
                }
            },
            ...
        ]
    },
    "numbers": [
        {
            "name": "Ключ комбинированный колесный",
            "number": "995456070R",
            "index": 1,
            "relevance": "2015-01-01T00:00:00.000Z",
            "count": [
                {
                    "count": "1",
                    "title": "для Lada X-Ray"
                }
            ],
            "coordinates": [
                {
                    "top": {
                        "x": 634,
                        "y": 6
                    },
                    "bottom": {
                        "x": 670,
                        "y": 46
                    }
                }
            ]
        },
        ...
    ],
    "breadcrumbs": [
        ...
        ,{
            "name": "Инструмент",
            "url": "3373769"
        }
    ],
    "next": {
        "name": "Трансмиссия - Коробка передач, сцепление",
        "type": "CARS_NATIVE",
        "mark": "VAZ",
        "model": "58961",
        "short_name": 3373667
    },
    "prev": {
        "name": "Механизмы управления - Тормоза, сцепление (привод, механизмы)",
        "type": "CARS_NATIVE",
        "mark": "VAZ",
        "model": "58961",
        "short_name": 3373722
    }
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
| years | string |  |
| index | integer | Порядковый номер |
| relevance | string (date) | Применяемость |
| image | string | URL изображения |

### Значения group

| Имя | Тип | Используется в URL| Описание |
| :---- | :------: | :------: | :--------------- |
| short_name | integer | - | Идентификатор |
| name | string | - | Наименование |
| coordinates | array | - | Координаты других группп |
| coordinates[..].name | string | - | Название точки на изображении |
| coordinates[..].group_short_name | integer | Да | Идентификатор группы-ссылки |
| coordinates[..].coordinate.bottom.x | integer | Нижний Х |
| coordinates[..].coordinate.bottom.y | integer | Нижний У |
| coordinates[..].coordinate.top.x | integer | Верхний Х |
| coordinates[..].coordinate.top.y | integer | Верхний У |

### Значения numbers

| Имя | Тип | Описание |
| :---- | :------: | :--------------- |
| id | integer | Идентификатор |
| name | string | Наименование |
| number | string | Номер |
| index | integer | Порядковый номер |
| relevance | string (date) | Применяемость |
| count | array | Счетчики |
| count[..].count | string | Кол-Во |
| count[..].title | string | Принадлежность |
| coordinates | array | Координаты |
| coordinates[..].bottom | object | Нижние точки |
| coordinates[..].bottom.x | integer | Нижний Х |
| coordinates[..].bottom.y | integer | Нижний У |
| coordinates[..].top | object | Верхние точки |
| coordinates[..].top.x | integer | Верхний Х |
| coordinates[..].top.y | integer | Верхний У |

### Значения breadcrumbs

| Имя | Тип | Описание |
| :---- | :------: | :--------------- |
| name | string | Имя хлебной крошки |
| url | string | адрес текущей хлебной крошки |
