# Модели (models)

## `GET /:mark/:country_short_name`

Возвращает объект с двумя массивами models и breadcrumbs

### Примеры

| Конечная точка | Описание |
| :---- | :--------------- |
| GET /NISSAN/EL | Модели марки Nissan Европа (лев) |
| GET /INFINITI/ER | Модели марки Infiniti Европа (прав) |

### Пример запроса

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/CARS_FOREIGN/NISSAN/EL
```

### Пример ответа

```json
{
    "models": [
        {
           "type": "CARS_FOREIGN",
           "mark": "NISSAN",
           "country_short_name": "EL",
           "model": "PRIMERA",
           "serial": "P12E",
           "directory": "001",
           "from_date": "2002-01-01T00:00:00.000Z",
           "to_date": "2007-05-01T00:00:00.000Z"
        },
        ...
    ],
    "breadcrumbs": [
        ...
        ,{
            "name": "Европа (лев)",
            "url": "EL"
        }
    ]
}
```

### Значения models

| Имя точка | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| type | string | Да | Тип машины (всегда CARS_FOREIGN) |
| mark | string | Да | Название марки (NISSAN или INFINITI) |
| country_short_name | string | Да | Сокращение страны (например: AR / GL ) |
| directory | string | Да | Техсимвольное число содержашее в себе текущую модель+серию |
| model | string | - | Название модели (например ATLAS) |
| serial | string | - | Серия модели (например F22, F23, F24) |
| from_date | null/Date | - | Дата производства "от" |
| to_date | null/Date | - | Дата производства "до" |

### Значения breadcrumbs

| Имя точка | Тип | Описание |
| :---- | :------: | :--------------- |
| name | string | Имя хлебной крошки |
| url | string | адрес текущей хлебной крошки |


## `GET /:mark/:country_short_name/:directory`

Для перехода к списку модификаций нужно выбрать модель и передать ее сокращение (directory) в GET параметры