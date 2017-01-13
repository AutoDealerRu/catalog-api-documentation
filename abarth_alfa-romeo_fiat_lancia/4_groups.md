# Группы

## `GET /:mark/:model_short_name/:modification_short_name/:unit_short_name`

Возвращает объект с двумя или тремя массивами groups, breadcrumbs и abbreviations (рассшифровка сокращений, если есть)

| Конечная точка | Описание |
| :---- | :--------------- |
| GET /CARS_FOREIGN/ABARTH | Серии марки Abarth Легковых иномарок |
| GET /CARS_FOREIGN/ALFA-ROMEO | Серии марки Alfa-Romeo Легковых иномарок |
| GET /CARS_FOREIGN/FIAT | Серии марки Fiat Легковых иномарок |
| GET /CARS_FOREIGN/LANCIA | Серии марки Lancia Легковых иномарок |

### Пример запроса

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/CARS_FOREIGN/FIAT/CIN/3P/101
```

### Пример ответа

```json
{
    "abbreviations": [
        {
            "abbreviation": "025",
            "description": "CLIMATE CONTROL 1"
        }
        ...
    ],
    "groups": [
        {
            "short_name": 1,
            "full_name": "БЛОК И ГОЛОВКА ЦИЛИНДРОВ",
            "modification_short_name": "3P",
            "unit_short_name": 101,
            "subgroups": [
                {
                    "id": "10101%2F08",
                    "id_raw": "10101/08",
                    "description": "БЛОК И ГОЛОВКА ЦИЛИНДРОВ",
                    "variant": 1,
                    "revision": 0,
                    "applicability": "CC1.2+CMBBZ",
                    "applicabilities": [
                        "CC1.2",
                        "CMBBZ"
                    ]
                }
                ...
            ]
        }
        ...
    ],
    "breadcrumbs": [
        ...
        {
            "name": "БЛОК И ГОЛОВКА ЦИЛИНДРОВ",
            "url": "101"
        }
    ]
}
```

### Значения abbreviations

| Имя | Тип | Описание |
| :---- | :------: | :------: | :--------------- |
| abbreviation | string | Идентификатор |
| description | string | Рассшифровка |

### Значения groups

| Имя | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| short_name | integer | - | Идентификатор |
| full_name | string | - | Наименование |
| modification_short_name | string | - | Идентификатор модификации |
| unit_short_name | integer | - | Идентификатор основного узла |
| subgroups | string | - | Подгруппы |
| subgroups.id | string | Да | Идентификатор (urlencoded) |
| subgroups.id_raw | string | Да | Идентификатор (без urlencode) |
| subgroups.description | string | - | Описание |
| subgroups.variant | integer | - | Вариант |
| subgroups.revision | integer | - | Ревизия |
| subgroups.applicability | string | - | Применяемость без форматирования |
| subgroups.applicabilities[..] | array | - | Применяемость |

### Значения breadcrumbs

| Имя | Тип | Описание |
| :---- | :------: | :--------------- |
| name | string | Имя хлебной крошки |
| url | string | адрес текущей хлебной крошки |


## `GET /:mark/:model_short_name/:modification_short_name/:short_name/:id`

Для перехода к списку деталей нужно выбрать подгруппу и передать ее id (subgroups.id) в GET параметры  
Внимание! Необходимо следовать редиректам