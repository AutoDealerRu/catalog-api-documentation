# Модели (models)

## `GET /:type/:mark/:country/:aggregation`

Возвращает объект с двумя массивами models и breadcrumbs

| Конечная точка | Описание |
| :---- | :--------------- |
| GET /CARS_FOREIGN/MERCEDES_BENZ/EU/FG | Модели марки MERCEDES BENZ Европа Шасси |
| GET /CARS_FOREIGN/SMART/SM/M | Модели марки Smart Двигатель |

### Пример запроса

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/CARS_FOREIGN/MERCEDES_BENZ/EU/FG
```

### Пример ответа

```json
{
    "models": [
        {
            "type": "CARS_FOREIGN",
            "mark": "MERCEDES_BENZ",
            "country": "EU",
            "aggregation": "FG",
            "model": "100012",
            "catalog": "050",
            "model_formatted": "100.012",
            "modification": "600",
            "name": "PASSENGER CAR,LIMOUSINE,FOUR-DOOR,3200 MM WHEELBASE",
            "from_date": null,
            "to_date": null,
            "remark": null
        },
        ...
    ],
    "breadcrumbs": [
        ...
        ,{
            "name": "Европа",
            "url": "EU"
        },{
            "name": "Шасси",
            "url": "FG"
        }
    ]
}
```

### Значения models

| Имя точка | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| type | string | Да | Тип машины (всегда CARS_FOREIGN) |
| mark | string | Да | Название марки (NISSAN или INFINITI) |
| country | string | Да | Сокращение страны (например: EU / US ) |
| aggregation | string | Да | Сокращение агрегата (например: FG / M ) |
| model | string | Да | Сокращение модели |
| catalog | string | Да | Код каталога |
| model_formatted | string | - | Идентификатор модели |
| modification | string | - | Информация о модификации |
| name | string | - | Имя модели |
| from_date | null / Date | - | Дата начала производства |
| to_date | null / Date | - | Дата окончания производства |
| remark | null / String | - | Дополнительная информация |

### Значения breadcrumbs

| Имя точка | Тип | Описание |
| :---- | :------: | :--------------- |
| name | string | Имя хлебной крошки |
| url | string | адрес текущей хлебной крошки |


## `GET /:type/:mark/:country/:aggregation/:model/:catalog`

Для перехода к списку моделей нужно выбрать модель (model) и каталог (catalog) и передать их в GET параметры