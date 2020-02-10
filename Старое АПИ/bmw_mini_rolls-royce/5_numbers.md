# Номера деталей

## `GET /:mark/:series_short_name/:model_short_name/:rule_position/:transmission/:group_number/:subgroup_short_name`

Возвращает объект с двумя массивами numbers, breadcrumbs и объектом subgroup

### Примеры

| Конечная точка | Описание |
| :---- | :--------------- |
| GET /BMW/E81/51382/LEFT/MANUAL/01/316004 | Группы марки BMW, семейства 1' E81, модели 116d с левый рулем и ручным КПП, группа Техническая литература, подгруппа Рук-во по эксплуат. E81, E87 без iDrive |
| GET /MINI/R50/48010/LEFT/MANUAL/01/339558 | Модели марки Mini, семейства MINI Clubman R55, модели Cooper с левым рулем и ручным КПП, группа Техническая литература, подгруппа Брошюра Service Kontakt MINI  |
| GET /ROLLS-ROYCE/RR4/52003/LEFT/AUTO/01/377326 | Модели марки Rolls-Royce, семейства MINI Ghost, модели Ghost с левым рулем и ручным КПП, группа Техническая литература, подгруппа Руководство по эксплуатации RR4 |

### Пример запроса

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/CARS_FOREIGN/BMW/E81/51382/LEFT/MANUAL/01/316004
```

### Пример ответа

```json
{
    "subgroup": {
        "short_name": 316004,
        "name": "Рук-во по эксплуат. E81, E87 без iDrive",
        "image": "https://acat.online/catalogs/CARS_FOREIGN/BMW/E81/51382/LEFT/MANUAL/01/316004/image",
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
    "numbers": [
        {
            "number": "01 40 2601706",
            "full_name": "Рук-во по эксплуат. E81, E87 без iDrive",
            "options": "DE, MJ 2009",
            "quantity": 1,
            "position": 8,
            "model_short_name": 51382,
            "date_start": "2009-03-01T00:00:00.000Z",
            "date_end": "2009-09-01T00:00:00.000Z",
            "rule_position": "LEFT",
            "group_number": "01",
            "subgroup_short_name": 316004,
            "before": "Для автомобилей с Система навигации Business и Система навигации Professional",
            "after": "только в комбинации с",
            "coordinate": {
                "bottom": {
                    "x": 434,
                    "y": 81
                },
                "top": {
                    "x": 375,
                    "y": 25
                }
            },
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

### Значения numbers

| Имя | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| number | string | - | Номер детали |
| full_name | string | - | Наименование детали |
| options | string | - | Дополнительные опции |
| quantity | integer | - | Количество |
| position | integer | - | Порядковый номер |
| model_short_name | integer | - | Идентификатор модели |
| date_start | string | - | Дата начала производства |
| date_end | string | - | Дата окончания производства |
| rule_position | string | - | Позиция руля |
| group_number | string | - | Идентификатор группы |
| subgroup_short_name | integer | - | Идентификатор подгруппы |
| before | string | - | Рекомендации перед работой |
| after | string | - | Рекомендации после работы |
| coordinate | object | - | Координаты |
| coordinate.bottom | object | - | Верхняя левая точка |
| coordinate.bottom.x | integer | - | Верхняя левая точка x |
| coordinate.bottom.y | integer | - | Верхняя левая точка y |
| coordinate.top | object | - | Нижняя правая точка |
| coordinate.top.x | integer | - | Нижняя правая точка x |
| coordinate.top.y | integer | - | Нижняя правая точка y |
| coordinate.transmissions | array | - | КПП |


### Значения breadcrumbs

| Имя | Тип | Описание |
| :---- | :------: | :--------------- |
| name | string | Имя хлебной крошки |
| url | string | адрес текущей хлебной крошки |