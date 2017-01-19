# Группы (countries) и сервисы (services)

## `GET /:type/:mark/:country_short_name/:model/:year/:catalog_code/:dir`

Возвращает объект с массивами groups, services, breadcrumbs и объектом model

| Конечная точка | Описание |
| :---- | :--------------- |
| GET /CARS_FOREIGN/AUDI/RA/A1/2014/708/R | Группы и сервисы модели Audi A1 (Аргентина) |

### Пример запроса

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/CARS_FOREIGN/AUDI/RA/A1/2014/708/R
```

### Пример ответа

```json
{
    "breadcrumbs": [
        ...
        {
            "name": "Audi A1",
            "url": "A1"
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
    "groups": [
        {
            "dir": "R",
            "catalog_code": "708",
            "year": "2014",
            "model": "A1",
            "country_short_name": "RA",
            "type": "CARS_FOREIGN",
            "mark": "AUDI",
            "group": "0",
            "name": "Аксессуары, Infotainment",
            "img": "0.png"
        },
        ...
    ],
    "services": [
        {
            dir": "R",
            "catalog_code": "708",
            "year": "2014",
            "model": "A1",
            "country_short_name": "RA",
            "type": "CARS_FOREIGN",
            "mark": "AUDI",
            "service": 200,
            "name": "Расходные детали",
            "img": "200.png"
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

### Значения groups

| Имя точка | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| type | string | Да | Тип машины (в данном каталоге только CARS_FOREIGN - легковые иномарки) |
| mark | string | Да | Название марки (AUDI, SEAT, SKODA или VOLKSWAGEN) |
| country_short_name | string | Да | Сокращение страны (например: USA / MEX ) |
| model | string | Да | Название модели |
| year | Integer | Да | Год |
| catalog_code | string | Да | Код каталога |
| dir | string | Да | Директория (используется в get-параметрах) |
| group | string | Да | Код группы |
| name | string | - | Название группы |
| img | string | - | Картинка |

### Значения services

| Имя точка | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| type | string | Да | Тип машины (в данном каталоге только CARS_FOREIGN - легковые иномарки) |
| mark | string | Да | Название марки (AUDI, SEAT, SKODA или VOLKSWAGEN) |
| country_short_name | string | Да | Сокращение страны (например: USA / MEX ) |
| model | string | Да | Название модели |
| year | Integer | Да | Год |
| catalog_code | string | Да | Код каталога |
| dir | string | Да | Директория (используется в get-параметрах) |
| service | string | Да | Код группы сервиса |
| name | string | - | Название сервиса |
| img | string | - | Картинка |

## `GET /:type/:mark/:country_short_name/:model/:year/:catalog_code/:dir/group/:group`

Для перехода к списку подгрупп нужно передать в передеть код группы (group/:group) в GET параметры

## `GET /:type/:mark/:country_short_name/:model/:year/:catalog_code/:dir/service/:service`

Для перехода к списку подгрупп сервисов нужно передать в передеть код сервиса (service/:service) в GET параметры





