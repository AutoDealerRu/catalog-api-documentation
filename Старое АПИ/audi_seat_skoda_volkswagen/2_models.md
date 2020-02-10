# Страны (countries)

## `GET /:type/:mark/:country_short_name`

Возвращает объект с двумя массивами models и breadcrumbs

| Конечная точка | Описание |
| :---- | :--------------- |
| GET /CARS_FOREIGN/AUDI/RA | Модели марки AUDI (Аргентина) |

### Пример запроса

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/CARS_FOREIGN/AUDI/RA
```

### Пример ответа

```json
{
    "models": [
        {
            "dir": "R",
            "type": "CARS_FOREIGN",
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
                    "number_chassis": ""
                },
                ...
            ]
        },
        ...
    ],
    "breadcrumbs": [
        ...
        ,{
             "name": "Аргентина",
             "url": "RA"
         }
    ]
}
```

### Значения models

| Имя точка | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| type | string | Да | Тип машины (в данном каталоге только CARS_FOREIGN - легковые иномарки) |
| mark | string | Да | Название марки (AUDI, SEAT, SKODA или VOLKSWAGEN) |
| country_short_name | string | Да | Сокращение страны (например: USA / MEX ) |
| country_full_name | string | - | Название страны |
| dir | string | Да | Директория (используется в get-параметрах) |
| name | string | Да | Название модели |
| full_name | string | - | Полное название модели |
| date_start | string (date) | - | Дата производства "от" |
| date_end | string (date) | - | Дата производства "до" |
| production | string | - | Производство |
| years[] | array | - | Года производства |
| years[].catalog_code | Integer | - | Каталог |
| years[].year | Integer | - | Год |
| years[].number_chassis | string | - | Шасси |

### Значения breadcrumbs

| Имя точка | Тип | Описание |
| :---- | :------: | :--------------- |
| name | string | Имя хлебной крошки |
| url | string | адрес текущей хлебной крошки |

## `GET /:type/:mark/:country_short_name/:model/:year/:catalog_code/:dir`

Для перехода к списку групп нужно выбрать год производства модели  и передать название модели (model), год производства (year), каталог (catalog_code), директорию (dir) в GET параметры
