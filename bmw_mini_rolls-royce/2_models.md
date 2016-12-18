# Модели

## `GET /:mark/:series_short_name`

Возвращает объект с двумя массивами categories и breadcrumbs

### Примеры

| Конечная точка | Описание |
| :---- | :--------------- |
| GET /BMW/E81 | Модели марки BMW, семейства 1' E81 |
| GET /MINI/R55 | Модели марки Mini, семейства MINI Clubman R55 |
| GET /ROLLS-ROYCE/RR4 | Модели марки Rolls-Royce, семейства MINI Ghost |

### Пример запроса

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/CARS_FOREIGN/BMW/E81
```

### Пример ответа

```json
{
    "categories": [
        {
            "markets": [
                {
                    "models": [
                        {
                            "name": "116d",
                            "short_name": 51382,
                            "index": 1,
                            "market_code": "ECE",
                            "market_name": "ЕЭК",
                            "category_short_name": "HC",
                            "catalog_type": "VT",
                            "series_short_name": "E81",
                            "date_start": "2008-11-01T00:00:00.000Z",
                            "date_end": "2011-12-01T00:00:00.000Z",
                            "options": [
                                {
                                    "rule_position": "LEFT",
                                    "transmissions": [
                                        "MANUAL",
                                        "AUTO"
                                    ]
                                },
                                {
                                    "rule_position": "RIGHT",
                                    "transmissions": [
                                        "MANUAL",
                                        "AUTO"
                                    ]
                                }
                            ]
                        },
                        ...
                    ]
                },
                ...
            ],
        },
        ...
    ],
    "breadcrumbs": [
        ...
        {
            "name": "1' E81",
            "url": "E81"
        }
    ]
}
```

### Значения models

| Имя | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| categories | array | - | Категории транспортного средства |
| categories[..].short_name | string | - | Идентификатор категории транспортного средства |
| categories[..].name | string | - | Название категории |
| categories[..].catalog_type | string | - | Тип каталога |
| categories[..].series_short_name | string | - | Идентификатор серии |
| categories[..].image | string | - | URL категории транспортного средства |
| categories[..].markets | array | - | Список рынков, на которых производились транспортные средства |
| categories[..].markets[..].name | string | - | Название рынка |
| categories[..].markets[..].code | string | - | Идентификатор рынка |
| categories[..].markets[..].models | array | - | Модели |
| categories[..].markets[..].models[..].name | string | - | Название модели |
| categories[..].markets[..].models[..].short_name | string | Да | Идентификатор модели |
| categories[..].markets[..].models[..].index | string | - | Порядковый номер модели |
| categories[..].markets[..].models[..].market_code | string | - | Идентификатор рынка |
| categories[..].markets[..].models[..].market_name | string | - | Название рынка |
| categories[..].markets[..].models[..].category_short_name | string | - | Идентификатор категории |
| categories[..].markets[..].models[..].catalog_type | string | - | Тип каталога (enum, VT - современный каталог, ST - живая традиция) |
| categories[..].markets[..].models[..].series_short_name | string | - | Идентификатор серии |
| categories[..].markets[..].models[..].date_start | Date | - | Дата начала производства модели |
| categories[..].markets[..].models[..].date_end | Date | - | Дата окончания производства модели |
| categories[..].markets[..].models[..].options | string | - | Опции модели |
| categories[..].markets[..].models[..].options[..].rule_position | string | Да | Позиция руля (слева, справа, для мотоциклов - посередине) |
| categories[..].markets[..].models[..].options[..].transmissions | array | Да | КПП (автоматическая или ручная) |


### Значения breadcrumbs

| Имя | Тип | Описание |
| :---- | :------: | :--------------- |
| name | string | Имя хлебной крошки |
| url | string | адрес текущей хлебной крошки |


## `GET /:mark/:series_short_name/:short_name/:rule_position/:transmission`

Для перехода к списку групп нужно выбрать Модель, одну из его опций и передать их в GET параметры