# Модели (models)

## `GET /:type/:mark/:country_short/:family`

Возвращает объект с двумя массивами models и breadcrumbs

### Примеры

| Конечная точка | Описание |
| :---- | :--------------- |
| GET /KIA/EUR/CARENS | Модели марки KIA Европа CARENS |
| GET /HYUNDAI/USA/ELANTRA | Модели марки HYUNDAI США ELANTRA |

### Пример запроса

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/CARS_FOREIGN/KIA/EUR/CARENS
```

### Пример ответа

```json
{
    "models": [
        {
           "type": "CARS_FOREIGN",
           "mark": "KIA",
           "country_short": "EUR",
           "family": "CARENS",
           "model": "EURK1D006A",
           "model_name": "CARENS 06: -OCT.2006 (2006-2006)",
           "from_date": "2006-01-01T00:00:00.000Z",
           "to_date": "2006-01-01T00:00:00.000Z",
           "image": "KIA/Cutups/EURK1D00.rle"
        },
        ...
    ],
    "breadcrumbs": [
        ...
        ,{
            "name": "CARENS",
            "url": "CARENS"
        }
    ]
}
```

### Значения models

| Имя точка | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| type | string | Да | Тип кузова |
| mark | string | Да | Название марки (KIA или HYUNDAI) |
| country_short | string | Да | Сокращение страны (например: AUS / MES ) |
| family | string | Да | Семейство (одна модель может относится к нескольким семействам) |
| model | string | Да | Код модели |
| model_name | string | - | Название модели |
| from_date | null / date | - | Дата производства "от" |
| to_date | null / date | - | Дата производства "до" |
| image | string | - | Путьдо изображения |

### Значения breadcrumbs

| Имя точка | Тип | Описание |
| :---- | :------: | :--------------- |
| name | string | Имя хлебной крошки |
| url | string | адрес текущей хлебной крошки |


## `GET /:type/:mark/:country_short/:family/:model`

Для перехода к списку модификаций нужно выбрать модель и передать ее код (model) в GET параметры