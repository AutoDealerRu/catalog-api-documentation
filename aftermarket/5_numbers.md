# Номера (numbers)

## `GET /:type/:mark/:mark_short_name/:model_id/:modification_id/:group_id`

Возвращает объект с двумя массивам numbers и breadcrumbs

| Конечная точка | Описание |
| :---- | :--------------- |
| GET /CARS_FOREIGN/AFTERMARKET/AC/4211/12428/12096 | Номера AC ACE 4.6 Масла |

### Пример запроса

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/CARS_FOREIGN/AFTERMARKET/AC/4211/12428/12096
```

### Пример ответа

```json
{
    "numbers": [
        {
            "type": "CARS_FOREIGN",
            "mark": "AFTERMARKET",
            "mark_short_name": "AC",
            "model_id": 4211,
            "modification_id": 12428,
            "group_id": 12096,
            "provider": {
                "id": 11353,
                "name": "CARLUBE",
                "image": "https://212709.selcdn.ru/autocatalog-online/aftermarket/logos/11353"
            },
            "number": "XLS011",
            "name": "Масло осевого редуктора",
            "article_id": 129385604,
        },
        ...
    ],
    "breadcrumbs": [
        ...
        ,{
            "name": "Масла",
            "url": "12096"
        }
    ]
}
```

### Значения groups

| Имя точка | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| type | string | Да | Тип кузова |
| mark | string | Да | Название каталога (всегда будет AFTERMARKET) |
| mark_short_name | string | Да | Сокращенное название марки |
| model_id | integer | Да | Идентифкационный номер модели |
| modification_id | integer | Да | Идентифкационный номер модификации |
| group_id | integer | Да | Идентифкационный номер группы |
| provider | object | - | Производитель |
| provider.id | integer | Да | ID производителя |
| provider.name | string | - | Название производителя |
| provider.image | string | - | Путь до изображения производителя |
| number | string | Да | Номер |
| name | string | - | Название детали |
| article_id | integer | Да | ID артикула |

### Значения breadcrumbs

| Имя точка | Тип | Описание |
| :---- | :------: | :--------------- |
| name | string | Имя хлебной крошки |
| url | string | Адрес текущей хлебной крошки |


## `GET /:type/:mark/:mark_short_name/:model_id/:modification_id/:group_id/:provider.id/:number/:article_id`

### Для перехода к описанию номера нужно передать provider.id, number и article_id в GET параметры