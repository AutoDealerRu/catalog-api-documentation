# Модификации (modifications)

## `GET /:mark/:country_short_name/:directory`

Возвращает объект с двумя массивами modifications и breadcrumbs

### Примеры

| Конечная точка | Описание |
| :---- | :--------------- |
| GET /NISSAN/EL/298 | Модификации Nissan Европа (лев) ALMERA JPN MAKE N16 |
| GET /INFINITI/ER/019 | Модификации Infiniti Европа (прав) G37 SEDAN V36 |

### Пример запроса

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/CARS_FOREIGN/NISSAN/EL/298
```

### Пример ответа

```json
{
    "modifications": [
        {
           "type": "CARS_FOREIGN",
           "mark": "NISSAN",
           "country_short_name": "EL",
           "model": "ALMERA JPN MAKE",
           "serial": "N16",
           "directory": "298",
           "modification": 1,
           "from_date": "2000-04-01T00:00:00.000Z",
           "to_date": "1970-01-01T00:00:00.000Z",
           "body": "S",
           "engine": "QG18DE",
           "drive": null,
           "transmission": "AT",
           "other": [
               {
                   "name": "GRADE",
                   "value": "GX"
               }
           ]
        },
        ...
    ],
    "breadcrumbs": [
        ...
        ,{
            "name": "ALMERA JPN MAKE N16",
            "url": "298"
        }
    ]
}
```

### Значения modifications

| Имя точка | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| type | string | Да | Тип машины (всегда CARS_FOREIGN) |
| mark | string | Да | Название марки (NISSAN или INFINITI) |
| country_short_name | string | Да | Сокращение страны (например: AR / GL ) |
| directory | string | Да | Техсимвольное число содержашее в себе текущую модель+серию |
| modification | integer | Да | Номер модификации |
| model | string | - | Название модели (например ATLAS) |
| serial | string | - | Серия модели (например F22, F23, F24) |
| from_date | null/Date | - | Дата производства "от" |
| to_date | null/Date | - | Дата производства "до" |
| body | null/string | - | Кузов |
| engine | null/string | - | Двигатель |
| drive | null/string | - | Привод |
| transmission | null/string | - | Трансмиссия |
| other | array | - | остальные характеристики (array of objects) |
| other.name | string | - | Имя характеристики |
| other.value | string | - | Значение характеристики |

### Значения breadcrumbs

| Имя точка | Тип | Описание |
| :---- | :------: | :--------------- |
| name | string | Имя хлебной крошки |
| url | string | адрес текущей хлебной крошки |


## `GET /:mark/:country_short_name/:directory/:modification`

Для перехода к списку групп нужно выбрать модификацию и передать ее сокращение (modification) в GET параметры