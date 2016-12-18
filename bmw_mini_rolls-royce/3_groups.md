# Группы

## `GET /:mark/:series_short_name/:model_short_name/:rule_position/:transmission`

Возвращает объект с двумя массивами groups и breadcrumbs

### Примеры

| Конечная точка | Описание |
| :---- | :--------------- |
| GET /BMW/E81/51382/LEFT/MANUAL | Группы марки BMW, семейства 1' E81, модели 116d с левый рулем и ручным КПП |
| GET /MINI/R50/48010/LEFT/MANUAL | Модели марки Mini, семейства MINI Clubman R55, модели Cooper с левым рулем и ручным КПП  |
| GET /ROLLS-ROYCE/RR4/52003/LEFT/AUTO | Модели марки Rolls-Royce, семейства MINI Ghost, модели Ghost с левым рулем и ручным КПП |

### Пример запроса

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/CARS_FOREIGN/BMW/E81/51382/LEFT/MANUAL
```

### Пример ответа

```json
{
    "groups": [
        {
            "number": "01",
            "name": "Техническая литература",
            "image": "99291_t.jpg",
            "series_short_name": "E81",
            "catalog_type": "VT",
            "category_short_name": "HC",
            "model_short_name": 51382,
            "market_code": "ECE",
            "rule_position": "LEFT",
            "transmissions": [
                "MANUAL"
            ]
        },
        ...
    ],
    "breadcrumbs": [
        ...
        {
            "name": "116d",
            "url": "51382/LEFT/MANUAL"
        }
    ]
}
```

### Значения groups

| Имя | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| number | string | - | Номер группы |
| name | string | - | Название группы |
| image | string | - | URL изображения группы |
| series_short_name | string | - | Идентификатор серии |
| catalog_type | string | - | Тип каталога (enum, VT - современный каталог, ST - живая традиция) |
| category_short_name | string | - | Индентификатор категории |
| market_code | string | - | Индентификатор рынка |
| rule_position | string | - | Позиция руля (LEFT, MIDDLE, RIGHT) |
| transmissions | array | - | КПП (MANUAL, AUTO) |


### Значения breadcrumbs

| Имя | Тип | Описание |
| :---- | :------: | :--------------- |
| name | string | Имя хлебной крошки |
| url | string | адрес текущей хлебной крошки |


## `GET /:mark/:series_short_name/:model_short_name/:rule_position/:transmission/:number`

Для перехода к списку подгрупп нужно выбрать группу и передать его number в GET параметры