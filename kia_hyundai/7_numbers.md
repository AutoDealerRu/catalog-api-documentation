# Номера (subgroups)

## `GET /:type/:mark/:country_short/:family/:model/:modification/:group/:subgroup`

Возвращает объект с image (object) и массивами numbers, breadcrumbs

### Примеры

| Конечная точка | Описание |
| :---- | :--------------- |
| GET /CARS_FOREIGN/KIA/EUR/CARENS/EURK1D006A/BKWDS65/AC/AC004457EU | Номера для CARENS 06 (2006-2006) BKWDS65 Аксессуары AC-001-EU TOW BAR |

### Пример запроса

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/CARS_FOREIGN/KIA/EUR/CARENS/EURK1D006A/BKWDS65/AC/AC004457EU
```

### Пример ответа

```json
{
    "image": {
        "type": "CARS_FOREIGN",
        "mark": "KIA",
        "country_short": "EUR",
        "family": "CARENS",
        "model": "EURK1D006A",
        "modification": "BKWDS65",
        "group": "AC",
        "subgroup": "AC004457EU"
    },
    "numbers": [
        {
            "label": "KME1DA",
            "number_type": "NUMBER",
            "number": "KME1D6000",
            "name": "TOW BAR",
            "coordinate": {
                "bottom": {
                    "y": 442,
                    "x": 605
                },
                "top": {
                    "y": 70,
                    "x": 10
                }
            },
            "count": "1",
            "from_date": "2006-06-01T00:00:00.000Z",
            "to_date": null,
            "description": [
                {
                    name: 'Привод',
                    value: '2WD'
                },
                ...
            ],
            "options": [
                'AT KNOB - LEATHER WRAPPED+WOOD GRAIN',
                'Some option 2',
                ...
            ],
            "color": {
                "name" : "Интерьер",
                "value" : "BLACK"
            }
        },
        ...,
        {
            "type": "CARS_FOREIGN",
            "mark": "KIA",
            "country_short": "GEN",
            "family": "RIO",
            "model": "GENK1G005A",
            "modification": "BNFGN65",
            "group": "BO",
            "subgroup": "6066011",
            "label": "60-660",
            "number_type": "SECTION",
            "group_name": "Кузовная",
            "subgroup_name": "60-660  крылья и панель капота",
            "image": "KIA/Thumb/GENK1G00/6066011.png",
            "coordinate": {
                "bottom": {
                    "y": 136,
                    "x": 451
                },
                "top": {
                    "y": 122,
                    "x": 368
                }
            }
        }
    ],
    "breadcrumbs": [
        ...
        ,{
            "name": "AC-001-EU  TOW BAR",
            "url": "AC004457EU"
        }
    ]
}
```

### Значения image

| Имя точка | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| type | string | Да | Тип кузова |
| mark | string | Да | Название марки (KIA или HYUNDAI) |
| country_short | string | Да | Сокращение страны (например: AUS / MES ) |
| family | string | Да | Семейство (одна модель может относится к нескольким семействам) |
| model | string | Да | Название модели (например ATLAS) |
| modification | string | Да | Номер модификации |
| group | string | Да | Сокращение группы |
| subgroup | string | Да | Сокращение подгруппы |

#### Пример запроса загрузки изображения
#### `GET /:type/:mark/:country_short/:family/:model/:modification/:group/:subgroup/image`
```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/CARS_FOREIGN/KIA/EUR/CARENS/EURK1D006A/BKWDS65/AC/AC004457EU/image
```
#### В ответ придет изображение, если статус 200 (схема) или 404 ("изображение не найдено", с изображением - заглушкой)

### Значения numbers (number_type = 'NUMBER')

| Имя точка | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| label | string | - | Обозначение на изображении |
| number_type | string | - | Тип номера (NUMBER - номер, SECTION - ссылка на другое изображение) |
| number | string | - | Номер (артикул) детали |
| name | string | - | Название детали |
| coordinate | object | - | Координаты |
| coordinate.bottom | object | - | Нижние точки |
| coordinate.bottom.x | integer | - | Нижний Х |
| coordinate.bottom.y | integer | - | Нижний У |
| coordinate.top | object | - | Верхние точки |
| coordinate.top.x | integer | - | Верхний Х |
| coordinate.top.y | integer | - | Верхний У |
| count | string | - | Количество (изредка содержит буквенное значение) |
| from_date | date / null | - | Дата начала производства |
| to_date | date / null | - | Дата окончания производства |
| description | array of object | - | Описание (может быть пустой массив) |
| description[0].name | string | - | Название описания |
| description[0].value | string | - | Значение описания |
| options | array of string | - | Опции (может быть пустой массив) |
| color | object | - | Цвет (может быть пустой) |
| color.name | string | - | Тип цвета |
| color.value | string | - | Значение цвета |

### Значения numbers (number_type = 'SECTION')

| Имя точка | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| type | string | Да | Тип кузова |
| mark | string | Да | Название марки (KIA или HYUNDAI) |
| country_short | string | Да | Сокращение страны (например: AUS / MES ) |
| family | string | Да | Семейство (одна модель может относится к нескольким семействам) |
| model | string | Да | Название модели (например ATLAS) |
| modification | string | Да | Номер модификации |
| group | string | Да | Сокращение группы |
| subgroup | string | Да | Сокращение подгруппы |
| label | string | - | Обозначение на изображении |
| number_type | string | - | Тип номера (NUMBER - номер, SECTION - ссылка на другое изображение) |
| group_name | string | - | Имя группы |
| subgroup_name | string | - | Имя подгруппы |
| image | string | - | Ссылка на изображение подгруппы |
| coordinate | object | - | Координаты |
| coordinate.bottom | object | - | Нижние точки |
| coordinate.bottom.x | integer | - | Нижний Х |
| coordinate.bottom.y | integer | - | Нижний У |
| coordinate.top | object | - | Верхние точки |
| coordinate.top.x | integer | - | Верхний Х |
| coordinate.top.y | integer | - | Верхний У |

#### Пример построения ссылки для номера - секции
#### `GET /:type/:mark/:country_short/:family/:model/:modification/:group/:subgroup`

### Значения breadcrumbs

| Имя точка | Тип | Описание |
| :---- | :------: | :--------------- |
| name | string | Имя хлебной крошки |
| url | string | адрес текущей хлебной крошки |