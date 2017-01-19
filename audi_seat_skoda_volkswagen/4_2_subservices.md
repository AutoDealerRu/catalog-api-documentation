# Подгруппы сервисов (subservices)

## `GET /:type/:mark/:country_short_name/:model/:year/:catalog_code/:dir/service/:service`

Возвращает объект с массивами subservices, breadcrumbs и объектами model, service

| Конечная точка | Описание |
| :---- | :--------------- |
| GET /CARS_FOREIGN/AUDI/RA/A1/2014/708/R/service/100 | Детали для устан. на сервисе для Audi A1 |

### Пример запроса

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/CARS_FOREIGN/AUDI/RA/A1/2014/708/R/service/100
```

### Пример ответа

```json
{
    "breadcrumbs": [
        ...
        {
           "name": "Детали для устан. на сервисе",
           "url": 100
        }
    ],
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
    "service": {
        "mark": "AUDI",
        "service": 100,
        "subservices": [
            "CCA",
            "COA",
            "COB",
            "MFC",
            "MFS",
            "NEG",
            "NEZ",
            "RCE",
            "RCK",
            "RCO",
            "RCP"
        ],
        "name": "Детали для устан. на сервисе",
        "img": "100.png"
    },
    "subservices": [
        {
            "service": "100",
            "dir": "R",
            "catalog_code": 708,
            "year": "2014",
            "model": "A1",
            "country_short_name": "RA",
            "type": "CARS_FOREIGN",
            "mark": "AUDI",
            "subservice": "CCA",
            "name": "Тормозные жидкости"
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

### Значения service

| Имя точка | Тип | Описание |
| :---- | :------: | :--------------- |
| mark | string  | Название марки (AUDI, SEAT, SKODA или VOLKSWAGEN) |
| service | string  | Код группы сервиса |
| name | string  | Название сервиса |
| img | string  | Картинка |
| subservices | array  | Список кодов подгрупп |

### Значения subservices

| Имя точка | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| type | string | Да | Тип машины (в данном каталоге только CARS_FOREIGN - легковые иномарки) |
| mark | string | Да | Название марки (AUDI, SEAT, SKODA или VOLKSWAGEN) |
| country_short_name | string | Да | Сокращение страны (например: USA / MEX ) |
| model | string | Да | Название модели |
| year | Integer | Да | Год |
| catalog_code | integer | Да | Код каталога |
| dir | string | Да | Директория (используется в get-параметрах) |
| service | string  | Код группы сервиса |
| subservice | string  | Код подгруппы сервиса |
| name | string  | Название подгруппы сервиса |

## `GET /:type/:mark/:country_short_name/:model/:year/:catalog_code/:dir/service/:service/:subservice`

Для перехода к списку деталей нужно передать номер Код подгруппы сервиса (subservice) в GET параметры



