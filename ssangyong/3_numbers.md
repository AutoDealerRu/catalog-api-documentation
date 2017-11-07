# Группы

## `GET /:mark/:model/:subgroup`

Возвращает объект с объектами (number, group, type, nextSubGroup, previousSubGroup, breadcrumbs)

### Пример запроса

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/CARS_FOREIGN/SSANGYONG/389410638/351476485
```

### Пример ответа

```json
{
    "number": {
        "positions": [
            {
                "code": "01",
                "number": "5211131000",
                "name": "PNL-SIDE OTR",
                "date_production": "01.03.2006 - 30.11.2007",
                "modification_count": "D20: 1E23: 1",
                "additional_info": "LH",
                "histories": [
                    ...
                    {
                        "number": "5211131010",
                        "type": "O",
                        "date_production": "01.12.2007 - ...",
                        "info": "08 M/Y,FASHION RAIL ADDED"
                    }
                ],
                "coordinates": [
                    {
                        "top": {
                            "x": 880,
                            "y": 443
                        },
                        "bottom": {
                            "x": 905,
                            "y": 468
                        }
                    }
                ]
            },
            ...
        ],
        "image": "https://acat.online/api/catalogs/CARS_FOREIGN/SSANGYONG/389410638/351476485/image",
        "subgroup_short_name": 351476485,
        "model_short_name": 389410638
    },
    "group": {
        "name": "Body",
        "short_name": 1633727457,
        "model_short_name": 389410638,
        "subgroups": [
            {
                "short_name": 1888337408,
                "name": "BODY MOUNTING"
            },
            ...
        ]
    },
    "type": "CARS_FOREIGN",
    "nextSubGroup": {
        "name": "Body - ROOF PANEL",
        "short_name": 46945316,
        "url": "/catalogs/CARS_FOREIGN/SSANGYONG/389410638/46945316"
    },
    "previousSubGroup": {
        "name": "Body - BODY MOUNTING",
        "short_name": 1888337408,
        "url": "/catalogs/CARS_FOREIGN/SSANGYONG/389410638/1888337408"
    },
    "breadcrumbs": [
        ...
        {
            "name": "Actyon",
            "url": "389410638"
        },
        {
            "name": "Body - SIDE & REAR BODY",
            "url": ""
        }
    ]
}
```

### Значения number

| Имя | Тип | Описание |
| :---- | :------: | :--------------- |
| image | string |  |
| subgroup_short_name | integer | Идентификатор подгруппы |
| model_short_name | array | Название модели |
| positions | array | Позиции |
| positions.code | string |  Код |
| positions.number | string | Номер |
| positions.name | string | Наименование |
| positions.date_production | string | Дата производства |
| positions.modification_count | string | Кол-во |
| positions.additional_info | string | Доп. информация |
| positions.histories | array | История замен |
| positions.histories.number | string | Номер |
| positions.histories.type | string | Тип |
| positions.histories.date_production | string | Дата производства |
| positions.histories.info | string | Информация |
| positions.coordinates | array | Координаты |
| positions.coordinates.top | string | Верхняя левая точка |
| positions.coordinates.top.x | string | x |
| positions.coordinates.top.y | string | y |
| positions.coordinates.bottom | string | Нижняя правая точка |
| positions.coordinates.bottom.x | string | x |
| positions.coordinates.bottom.y | string | y |

### Значения group

| Имя | Тип | Описание |
| :---- | :------: | :--------------- |
| name | string | Наименование группы |
| short_name | integer | Идентификатор группы |
| model_short_name | integer | Идентификатор модели |
| subgroups | array | Подгруппы |
| subgroups.short_name | integer | Идентификатор подгруппы |
| subgroups.name | array | Название подгруппы |

### Значения nextSubGroup, previousSubGroup

| Имя | Тип | Описание |
| :---- | :------: | :--------------- |
| name | string | Наименование подгруппы |
| short_name | integer | Идентификатор подгруппы |
| url | string | Ссылка на подгруппу |


### Значения breadcrumbs

| Имя | Тип | Описание |
| :---- | :------: | :--------------- |
| name | string | Имя хлебной крошки |
| url | string | адрес текущей хлебной крошки |
