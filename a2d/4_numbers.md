# Номера деталей

## `GET /:mark/:category/:model/:subgroup`

Возвращает объект с двумя массивами (numbers, breadcrumbs) и двумя объектами (model, group)

### Пример запроса

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/CARS_NATIVE/VAZ/GENERAL/58961/3373769
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
    "group": {
        "short_name": 3373769,
        "name": "Инструмент"
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
            ]
        }
        ...
    ],
    "breadcrumbs": [
        ...
        {
            "name": "Инструмент",
            "url": "3373769"
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

### Значения group

| Имя | Тип | Описание |
| :---- | :------: | :--------------- |
| short_name | integer | Идентификатор |
| name | string | Наименование |

### Значения numbers

| Имя | Тип | Описание |
| :---- | :------: | :--------------- |
| name | string | Наименование |
| number | string | Номер |
| index | integer | Порядковый номер |
| relevance | string (date) | Применяемость |
| count | array | Счетчики |
| count[..].count | string | Кол-Во |
| count[..].title | string | Принадлежность |

### Значения breadcrumbs

| Имя | Тип | Описание |
| :---- | :------: | :--------------- |
| name | string | Имя хлебной крошки |
| url | string | адрес текущей хлебной крошки |