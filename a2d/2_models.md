# Модели

## `GET /:mark/:category`

Возвращает объект с двумя массивами (models, breadcrumbs) и объектом mark

### Пример запроса

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/CARS_NATIVE/VAZ/GENERAL
```

### Пример ответа

```json
{
    "mark": {
        "type": "CARS_NATIVE",
        "full_name": "ВАЗ",
        "description": "Волжский автомобильный завод (Российская Федерация, г.Тольятти)",
        "url": "http://www.vaz.ru/",
        "category": "GENERAL",
        "short_name": "VAZ"
    },
    "models": [
        {
            "short_name": 58961,
            "name": "X-Ray",
            "name_with_mark": "ВАЗ X-Ray",
            "modification": "Lada XRay",
            "years": null,
            "index": 896,
            "relevance": null,
            "image": "58961.jpg"
        }
        ...
    ],
    "breadcrumbs": [
        ...
        {
            "name": "ВАЗ",
            "url": "VAZ"
        }
    ]
}
```

### Значения mark

| Имя | Тип | Описание |
| :---- | :------: | :--------------- |
| type | string | Тип транспортного средства |
| full_name | string | Наименование марки |
| description | string | Описание марки |
| url | string | URL производителя |
| category | string | Тип каталога |
| short_name | string | Идентификатор марки |

### Значения models

| Имя | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| short_name | integer | Да | Идентификатор |
| name | string | - | Наименование |
| name_with_mark | string | - | Наименование с маркой |
| modification | string | - | Модификация |
| years | string | - |  |
| index | integer | - | Порядковый номер |
| relevance | string (date) | - | Применяемость |
| image | string | - | URL изображения |

### Значения breadcrumbs

| Имя | Тип | Описание |
| :---- | :------: | :--------------- |
| name | string | Имя хлебной крошки |
| url | string | адрес текущей хлебной крошки |


## `GET /:mark/:category/:short_name`

Для перехода к списку групп нужно выбрать модель и передать ее идентификатор (short_name) в GET параметры