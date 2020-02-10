# Страны (countries)

## `GET /:type/:mark`

Возвращает объект с двумя массивами countries и breadcrumbs

| Конечная точка | Описание |
| :---- | :--------------- |
| GET /CARS_FOREIGN/TOYOTA | Страны марки TOYOTA |
| GET /CARS_FOREIGN/LEXUS | Страны марки LEXUS |

### Пример запроса

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/CARS_FOREIGN/TOYOTA
```

### Пример ответа

```json
{
    "countries": [
        {
            "type": "CARS_FOREIGN",
            "mark": "TOYOTA",
            "country_short_name": "US",
            "full_name": "США"
        },
        ...
    ],
    "breadcrumbs": [
        ...
        ,{
            "name": "TOYOTA",
            "url": "TOYOTA"
        }
    ]
}
```

### Значения countries

| Имя точка | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| type | string | - | Тип машины (в данном каталоге только CARS_FOREIGN - легковые иномарки) |
| mark | string | - | Название марки (TOYOTA или LEXUS) |
| country_short_name | string | Да | Сокращение страны (например: US / JP ) |
| full_name | string | - | Полное название страны |

### Значения breadcrumbs

| Имя точка | Тип | Описание |
| :---- | :------: | :--------------- |
| name | string | Имя хлебной крошки |
| url | string | адрес текущей хлебной крошки |


## `GET /:type/:mark/:country_short_name`

Для перехода к списку моделей нужно выбрать страну и передать ее сокращение (country_short) в GET параметры