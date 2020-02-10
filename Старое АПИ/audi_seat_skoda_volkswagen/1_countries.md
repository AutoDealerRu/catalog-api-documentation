# Страны (countries)

## `GET /:type/:mark`

Возвращает объект с двумя массивами countries и breadcrumbs

| Конечная точка | Описание |
| :---- | :--------------- |
| GET /CARS_FOREIGN/AUDI | Страны марки AUDI |
| GET /CARS_FOREIGN/SKODA | Страны марки SKODA |

### Пример запроса

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/CARS_FOREIGN/AUDI
```

### Пример ответа

```json
{
    "countries": [
        {
            "type": "CARS_FOREIGN",
            "country_short_name": "RA",
            "mark": "AUDI",
            "full_name": "Аргентина"
        },
        ...
    ],
    "breadcrumbs": [
        ...
        ,{
             "name": "AUDI",
             "url": "AUDI"
         }
    ]
}
```

### Значения countries

| Имя точка | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| type | string | - | Тип машины (в данном каталоге только CARS_FOREIGN - легковые иномарки) |
| mark | string | - | Название марки (AUDI, SEAT, SKODA или VOLKSWAGEN) |
| country_short_name | string | Да | Сокращение страны (например: USA / MEX ) |
| full_name | string | - | Полное название страны |

### Значения breadcrumbs

| Имя точка | Тип | Описание |
| :---- | :------: | :--------------- |
| name | string | Имя хлебной крошки |
| url | string | адрес текущей хлебной крошки |


## `GET /:type/:mark/:country_short_name`

Для перехода к списку моделей нужно выбрать страну и передать ее сокращение (country_short) в GET параметры