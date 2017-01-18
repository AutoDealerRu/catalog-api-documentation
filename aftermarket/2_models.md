# Модели (models)

## `GET /:type/:mark/:mark_short_name`

Возвращает объект с двумя массивами models и breadcrumbs

| Конечная точка | Описание |
| :---- | :--------------- |
| GET /CARS_FOREIGN/AFTERMARKET/AC | Модели марки AC |

### Пример запроса

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/CARS_FOREIGN/AFTERMARKET/AC
```

### Пример ответа

```json
{
    "models": [
        {
            "type": "CARS_FOREIGN",
            "mark": "AFTERMARKET",
            "mark_short_name": "AC"
            "model_id": 4209,
            "mark_name": "AC",
            "model_name_eng": "428 Convertible",
            "model_name_rus": "428 кабрио",
            "from_date": "1965-01-01T00:00:00.000Z",
            "to_date": "1974-12-01T00:00:00.000Z",
        },{
            "type": "CARS_FOREIGN",
            "mark": "AFTERMARKET",
            "mark_short_name": "AC"
            "model_id": 4208,
            "mark_name": "AC",
            "model_name_eng": "428 Fastback",
            "model_name_rus": null,
            "from_date": "1967-01-01T00:00:00.000Z",
            "to_date": "1974-12-01T00:00:00.000Z",
        },
        ...
    ],
    "breadcrumbs": [
        ...
        ,{
            "name": "AC",
            "url": "AC"
        }
    ]
}
```

### Значения models

| Имя точка | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| type | string | - | Тип кузова |
| mark | string | - | Название каталога (всегда будет AFTERMARKET) |
| mark_short_name | string | - | Сокращенное название марки |
| model_id | integer | Да | Идентифкационный номер модели |
| mark_name | string | - | Название марки (ACURA, HYUNDAI и т.д.) |
| model_name_eng | string | - | Название модели на английском |
| model_name_rus | null/string | - | Название модели на русском (может быть null) |
| from_date | null/date | - | Дата начала производства |
| to_date | null/date | - | Дата окончания производства |

### Значения breadcrumbs

| Имя точка | Тип | Описание |
| :---- | :------: | :--------------- |
| name | string | Имя хлебной крошки |
| url | string | Адрес текущей хлебной крошки |


## `GET /:type/:mark/:mark_short_name/:model_id`

Для перехода к списку модификаций нужно выбрать модель и передать ее идентификатор (model_id) в GET параметры