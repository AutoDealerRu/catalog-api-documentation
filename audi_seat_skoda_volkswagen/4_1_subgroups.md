# Подгруппы (subgroups)

## `GET /:type/:mark/:country_short_name/:model/:year/:catalog_code/:dir/group/:group`

Возвращает объект с массивами subgroups, breadcrumbs и объектами model, group

| Конечная точка | Описание |
| :---- | :--------------- |
| GET /CARS_FOREIGN/AUDI/RA/A1/2014/708/R/group/0 | Подгруппы Аксессуаров модели Audi A1 (Аргентина) |

### Пример запроса

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/CARS_FOREIGN/AUDI/RA/A1/2014/708/R/group/0
```

### Пример ответа

```json
{
    "breadcrumbs": [
        ...
        {
            "name": "Аксессуары, Infotainment",
            "url": "0"
        }
    ],
    "group": {
        "mark": "AUDI",
        "group": "0",
        "name": "Аксессуары, Infotainment",
        "img": "0.png"
    },
    "model": {
        "country_short_name": "RA",
        "country_full_name": "Аргентина",
        "mark": "AUDI",
        "name": "A1",
        "full_name": "Audi A1",
        "date_start": "2011-01-01T00:00:00.000Z",
        "date_end": "2014-01-01T00:00:00.000Z",
        "production": "B",
        "years": [
            {
                "year": 2014,
                "catalog_code": 708,
                "number_chassis": "",
                "groups": "1234567890"
            },
            ...
        ]
    },
    "subgroups": [
        {
            "mark": "AUDI",
            "dir": "R",
            "catalog_code": 708,
            "group": "0",
            "subgroup": "010",
            "detail": 10010,
            "name": "Таблички Подушка безопасности",
            "options": "",
            "filename": "620010100",
            "illustrate": "620/620010100.png"
        },
        ...
    ]
}
```

### Значения breadcrumbs

| Имя точка | Тип | Описание |
| :---- | :------: | :--------------- |
| name | string | Имя хлебной крошки |
| url | string | адрес текущей хлебной крошки |

### Значения group

| Имя точка | Тип | Описание |
| :---- | :------: | :--------------- |
| mark | string  | Название марки (AUDI, SEAT, SKODA или VOLKSWAGEN) |
| group | string  | Код группы |
| name | string | Название группы |
| img | string | Картинка |

### Значения model

| Имя точка | Тип | Описание |
| :---- | :------: | :--------------- |
| mark | string | Название марки (AUDI, SEAT, SKODA или VOLKSWAGEN) |
| country_short_name | string | Сокращение страны (например: USA / MEX ) |
| country_full_name | string | Название страны |
| name | string | Название модели |
| full_name | string | Полное название модели |
| date_start | string (date) | Дата производства "от" |
| date_end | string (date) | Дата производства "до" |
| production | string | Производство |
| years[] | array | Года производства |
| years[].catalog_code | Integer | Каталог |
| years[].year | Integer | Год |
| years[].number_chassis | string | Шасси |

### Значения subgroups

| Имя точка | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| type | string | Да | Тип машины (в данном каталоге только CARS_FOREIGN - легковые иномарки) |
| mark | string | Да | Название марки (AUDI, SEAT, SKODA или VOLKSWAGEN) |
| country_short_name | string | Да | Сокращение страны (например: USA / MEX ) |
| model | string | Да | Название модели |
| year | Integer | Да | Год |
| catalog_code | integer | Да | Код каталога |
| dir | string | Да | Директория (используется в get-параметрах) |
| group | string | Да | Код группы |
| subgroup | string | Да | Код подгруппы |
| detail | string | Да | Код группы деталей |
| name | string | - | Название подгруппы |
| options | string | - | Опции |
| illustrate | string | - | Иллюстрация |

## `GET /:type/:mark/:country_short_name/:model/:year/:catalog_code/:dir/group/:group/:subgroup/:detail`

Для перехода к списку деталей нужно передать Код подгруппы (subgroup), Код группы деталей (detail) в GET параметры