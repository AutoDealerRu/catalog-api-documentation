# Основные узлы

## `GET /:mark/:model_short_name/:modification_short_name/:unit_short_name/:subgroup_id`

Возвращает объект объектом подгруппы, номерами, рассшифровками и breadcrumbs

| Конечная точка | Описание |
| :---- | :--------------- |
| GET /CARS_FOREIGN/ABARTH | Серии марки Abarth Легковых иномарок |
| GET /CARS_FOREIGN/ALFA-ROMEO | Серии марки Alfa-Romeo Легковых иномарок |
| GET /CARS_FOREIGN/FIAT | Серии марки Fiat Легковых иномарок |
| GET /CARS_FOREIGN/LANCIA | Серии марки Lancia Легковых иномарок |

### Пример запроса

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/CARS_FOREIGN/FIAT/CIN/3P/101/10101%2F08/1
```

### Пример ответа

```json
{
    "id": "10101/08",
    "description": "БЛОК И ГОЛОВКА ЦИЛИНДРОВ",
    "variant": 1,
    "revision": "0",
    "modification": "",
    "modification_short_name": "3P",
    "unit_short_name": 101,
    "group_short_name": "1",
    "image": "https://acat.online/api/catalogs/CARS_FOREIGN/FIAT/CIN/3P/101/10101%2F08/1/image",
    "applicability": "CC1.2+CMBBZ",
    "applicabilities": [
        "CC1.2",
        "CMBBZ"
    ],
    "numbers": [
        {
            "index": 1,
            "number": "71740648",
            "description": "CYLINDER HEAD WITH VALVES",
            "amount": 1,
            "modification": "",
            "applicability": "!@MOT1",
            "modification_short_name": "3P",
            "unit_short_name": 101,
            "group_short_name": "1",
            "subgroup_id": "10101/08",
            "variant": 1,
            "applicabilities": [
                "@MOT1"
            ],
            "coordinate": {
                "top": {
                    "x": 8,
                    "y": 271
                },
                "bottom": {
                    "x": 32,
                    "y": 295
                }
            }
        }
        ...
    ],
    "abbreviations": [
        {
            "abbreviation": "40Q",
            "description": "LPG SUPPLY (STANDARD FOR ITALY)"
        }
        ...
    ],
    "breadcrumbs": [
        ...
        {
            "name": "БЛОК И ГОЛОВКА ЦИЛИНДРОВ",
            "url": "1"
        }
    ]
}
```

### Значения

| Имя | Тип | Описание |
| :---- | :------: | :--------------- |
| id | integer | Идентификатор подгруппы |
| description | string | Описание |
| variant | integer | Вариант |
| revision | integer | Ревизия |
| modification | string | Модификация |
| modification_short_name | string | Идентификатор модификации |
| unit_short_name | integer | Идентификатор основной группы |
| group_short_name | string | Идентификатор группы |
| image | string | URL иллюстрации |
| applicability | string | Применяемость без форматирования |
| applicabilities | array | Применяемость |
| numbers | string | Номера |
| numbers.index | integer | Порядковый номер |
| numbers.number | string | Номер |
| numbers.description | string | Описание |
| numbers.amount | integer | Количество |
| numbers.modification | string | Модификация |
| numbers.applicability | string | Применяемость без форматирования |
| numbers.modification_short_name | string | Идентификатор модификации |
| numbers.unit_short_name | integer | Идентификатор основной группы |
| numbers.group_short_name | string | Идентификатор группы |
| numbers.subgroup_id | string | Идентификатор подгруппы |
| numbers.variant | integer | Вариант |
| numbers.applicabilities | string | Применяемость |
| numbers.coordinate | object | Координата |
| numbers.coordinate.top | object | Верхняя левая |
| numbers.coordinate.top.x | integer | x |
| numbers.coordinate.top.y | integer | y |
| numbers.coordinate.bottom | object | Правая нижняя |
| numbers.coordinate.bottom.x | integer | x |
| numbers.coordinate.bottom.y | integer | y |

### Значения abbreviations

| Имя | Тип | Описание |
| :---- | :------: | :--------------- |
| abbreviation | string | Идентификатор |
| description | string | Рассшифровка |

### Значения breadcrumbs

| Имя | Тип | Описание |
| :---- | :------: | :--------------- |
| name | string | Имя хлебной крошки |
| url | string | адрес текущей хлебной крошки |
