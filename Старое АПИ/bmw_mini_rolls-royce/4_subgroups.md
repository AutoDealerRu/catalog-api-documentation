# Подгруппы

## `GET /:mark/:series_short_name/:model_short_name/:rule_position/:transmission/:group_number`

Возвращает объект с двумя массивами subgroups и breadcrumbs

### Примеры

| Конечная точка | Описание |
| :---- | :--------------- |
| GET /BMW/E81/51382/LEFT/MANUAL/01 | Группы марки BMW, семейства 1' E81, модели 116d с левый рулем и ручным КПП, группа Техническая литература |
| GET /MINI/R50/48010/LEFT/MANUAL/01 | Модели марки Mini, семейства MINI Clubman R55, модели Cooper с левым рулем и ручным КПП, группа Техническая литература  |
| GET /ROLLS-ROYCE/RR4/52003/LEFT/AUTO/01 | Модели марки Rolls-Royce, семейства MINI Ghost, модели Ghost с левым рулем и ручным КПП, группа Техническая литература |

### Пример запроса

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/CARS_FOREIGN/BMW/E81/51382/LEFT/MANUAL/01
```

### Пример ответа

```json
{
    "subgroups": [
        {
            "short_name": 316004,
            "name": "Рук-во по эксплуат. E81, E87 без iDrive",
            "image": "https://212709.selcdn.ru/autocatalog-online/BMW/w_grafik/316004_t.jpg",
            "index": 8844,
            "catalog_type": "VT",
            "series_short_name": "E81",
            "category_short_name": "HC",
            "model_short_name": 51382,
            "market_code": "ECE",
            "group_number": "01",
            "rule_position": "LEFT",
            "date_start": "2009-03-01T00:00:00.000Z",
            "date_end": null,
            "transmissions": [
                "MANUAL"
            ]
        },
        ...
    ],
    "breadcrumbs": [
        ...
        {
            "name": "Техническая литература",
            "url": "01/LEFT/MANUAL"
        }
    ]
}
```

### Значения groups

| Имя | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| short_name | integer | Да | Индентификатор |
| name | string | - | Наименование |
| image | string | - | URL изображения |
| index | integer | - | Порядковый номер |
| catalog_type | string | - | Тип каталога (enum, VT - современный каталог, ST - живая традиция) |
| series_short_name | string | - | Индентификатор серии |
| category_short_name | string | - | Индентификатор категории |
| model_short_name | integer | - | Индентификатор модели |
| market_code | string | - | Индентификатор рынка |
| group_number | string | - | Индентификатор группы |
| rule_position | string | - | Позиция руля |
| date_start | Date | - | Дата начала производства |
| date_end | Date | - | Дата окончания производства |
| transmissions | array | - | КПП |


### Значения breadcrumbs

| Имя | Тип | Описание |
| :---- | :------: | :--------------- |
| name | string | Имя хлебной крошки |
| url | string | адрес текущей хлебной крошки |


## `GET /:mark/:series_short_name/:model_short_name/:rule_position/:transmission/:group_number/:short_name`

Для перехода к списку групп нужно выбрать Модель, одну из его опций и передать его в GET параметры