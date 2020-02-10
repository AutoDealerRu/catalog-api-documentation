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
    "numbers": [
      {
          "model_short_name": 389410638,
          "subgroup_short_name": 351476485,
          "code": "01",
          "number": "5211131000",
          "name": "PNL-SIDE OTR",
          "date_production": "01.03.2006 - 30.11.2007",
          "modification_count": "D20: 1E23: 1",
          "additional_info": "LH",
          "histories": [
              {
                  "number": "5211131000",
                  "date_production": "01.03.2006 - 30.11.2007"
              },
              {
                  "number": "5211131010",
                  "type": "O",
                  "date_production": "01.12.2007 - ...",
                  "info": "08 M/Y,FASHION RAIL ADDED"
              }
          ]
      },
      ...
    ],
    "image": "https://acat.online/api/catalogs/CARS_FOREIGN/SSANGYONG/389410638/351476485/image",
    "labels": [
        {
            "index": "01",
            "title": "PNL-SIDE OTR (5211131000)",
            "top": {
                "x": 880,
                "y": 443
            },
            "bottom": {
                "x": 905,
                "y": 468
            }
        },
        ...
    ],
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
        },{
            "name": "Body - SIDE & REAR BODY",
            "url": ""
        }
    ]
}
```

### Значения numbers

| Имя | Тип | Описание |
| :---- | :------: | :--------------- |
| model_short_name | array | Название модели |
| subgroup_short_name | integer | Идентификатор подгруппы |
| code | string |  Код |
| number | string | Номер |
| name | string | Наименование |
| date_production | string | Дата производства |
| modification_count | string | Кол-во |
| additional_info | null/string | Доп. информация |
| histories | array | История замен |
| histories.number | string | Номер |
| histories.type | string | Тип |
| histories.date_production | string | Дата производства |
| histories.info | string | Информация |

### Значения image & labels

| Имя | Тип | Описание |
| :---- | :------: | :--------------- |
| index | string | Номер на изображении |
| title | string | Названием + артикул точки на изображении |
| top | string | Верхняя левая точка |
| top.x | string | x |
| top.y | string | y |
| bottom | string | Нижняя правая точка |
| bottom.x | string | x |
| bottom.y | string | y |

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
