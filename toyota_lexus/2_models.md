# Модели (models)

## `GET /:type/:mark/:country_short_name`

Возвращает объект с двумя массивами models и breadcrumbs

### Примеры

| Конечная точка | Описание |
| :---- | :--------------- |
| GET /CARS_FOREIGN/TOYOTA/US | Модели марки Toyota США |
| GET /CARS_FOREIGN/LEXUS/GR | Модели марки Lexus Ближний восток |

### Пример запроса

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/CARS_FOREIGN/TOYOTA/US
```

### Пример ответа

```json
{
    "models": [
        {
           "country_short_name": "US",
           "catalog_code": "671440",
           "mark": "TOYOTA",
           "model": "4-RUNNER TRUCK",
           "modifications": "RN5#,6#,7#,VZN6#,LN5#,6#",
           "prod_start": "1983-08-01T00:00:00.000Z",
           "prod_end": "1989-03-01T00:00:00.000Z"
        },
        ...
    ],
    "breadcrumbs": [
        ...
        ,{
            "name": "США",
            "url": "US"
        }
    ]
}
```

### Значения models

| Имя точка | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| mark | string | Да | Название марки (TOYOTA или LEXUS) |
| country_short_name | string | Да | Сокращение страны (например: US / JP ) |
| catalog_code | string | Да | Код каталога |
| model | string | - | Название модели |
| modifications | string | - | Модификации |
| prod_start | null/Date | - | Дата производства "от" |
| prod_end | null/Date | - | Дата производства "до" |

### Значения breadcrumbs

| Имя точка | Тип | Описание |
| :---- | :------: | :--------------- |
| name | string | Имя хлебной крошки |
| url | string | адрес текущей хлебной крошки |


## `GET /:type/:mark/:country_short_name/:catalog_code`

Для перехода к списку комлектаций нужно выбрать модель и передать код каталога (catalog_code) в GET параметры
