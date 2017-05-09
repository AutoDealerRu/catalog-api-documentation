# Номера

## `GET /:mark/:model/:modification/:category/:subgroup/:subnumber`

### Пример запроса

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/CARS_FOREIGN/RENAULT/61/3348/10042/58d87a7f28798c02743e915c
```

### Пример ответа

```json
{
  "image": "https://212709.selcdn.ru/autocatalog-online/renault/dessins/00135143.png",
  "positions": [
    {
      "index": 1,
      "number": "7701473559",
      "replacement": "7701473104",
      "name": "COMPLET BODY",
      "additional_information": "Код технических особенностей. = \\36/ или Код технических особенностей. = \\19/, ; Заводской номер автомобиля < MOD0106, Код технических особенностей. = \\8/ или Код технических особенностей. = \\29/ или Код технических особенностей. = \\40/ или Код технических особенностей. = \\27/ или Код технических особенностей. = \\26/ или Код технических особенностей. = \\25/ или Код технических особенностей. = \\24/ или Код технических особенностей. = \\41/ или Код технических особенностей. = \\4/ или Код технических особенностей. = \\30/ или Код технических особенностей. = \\9/ или Код технических особенностей. = \\20/ или Код технических особенностей. = \\3/, ; Заводской номер автомобиля < MOD0106, Размещение рулевого колеса = Левостороннее, Код технических особенностей. = \\0/,",
      "coordinates": [
        {
          "bottom": {
            "x": 471,
            "y": 26
          },
          "top": {
            "x": 453,
            "y": 8
          }
        }
      ]
    },
    {
      "index": 1,
      "number": "600503272R",
      "replacement": "",
      "name": "",
      "additional_information": "Технические и законодательные требования страны = TLARGE",
      "coordinates": [
        {
          "bottom": {
            "x": 471,
            "y": 26
          },
          "top": {
            "x": 453,
            "y": 8
          }
        }
      ]
    },
    {
      "index": 2,
      "number": "7711210531",
      "replacement": "",
      "name": "",
      "additional_information": "",
      "coordinates": [
        {
          "bottom": {
            "x": 803,
            "y": 804
          },
          "top": {
            "x": 785,
            "y": 786
          }
        }
      ]
    }
  ],
  "options": [
    {
      "name": "Заводской номер автомобиля",
      "options": [
        {
          "name": "< MOD0106",
          "subnumber_id": "58d87a7c28798c02743e915b"
        }
      ]
    },
    {
      "name": "Код технических особенностей.",
      "options": [
        {
          "name": "= \\8/",
          "subnumber_id": "58d87a7f28798c02743e915c"
        },
        {
          "name": "= \\27/",
          "subnumber_id": "58d87a8128798c02743e915d"
        },
        {
          "name": "= \\26/",
          "subnumber_id": "58d87a8328798c02743e915e"
        },
        ...
      ]
    },
    {
      "name": "Технические и законодательные требования страны",
      "options": [
        {
          "name": "= TLBRES",
          "subnumber_id": "58d87ad928798c02743e917f"
        },
        {
          "name": "= SSPG",
          "subnumber_id": "58d87adc28798c02743e9180"
        }
      ]
    }
  ],
  "related": [
    {
      "name": "N400112",
      "subnumber_id": "58d87adf28798c02743e9181"
    }
  ],
  "parent": {
    "breadcrumbs": [
      ...
      ,{
        "url": "29182",
        "name": "Кузов"
      }
    ],
    "mark_short_name": "RENAULT",
    "model_short_name": 7,
    "modification_short_name": 165,
    "category_short_name": 494,
    "subgroup_short_name": 29182,
    "image": "https://212709.selcdn.ru/autocatalog-online/renault/dessins/00135143.png",
    "type": "CARS_FOREIGN"
  },
  "breadcrumbs": [
    ...
    ,{
      "url": "29182",
      "name": "Кузов"
    }
  ]
}
```

### Значения

| Имя | Тип | Описание |
| :---- | :------: | :--------------- |
| image | string | Ссылка на изображение |
| parent.mark_short_name | string | Идентификатор марки |
| parent.model_short_name | integer | Идентификатор модели |
| parent.modification_short_name | integer | Идентификатор модификации |
| parent.category_short_name | integer | Идентификатор категории |
| parent.subgroup_short_name | integer | Идентификатор подгруппы |
| related | array | Подобное |
| related.name | integer | Наименование |
| related.subnumber_id | integer | Идентификатор страницы с номером |
| options | array | Опции |
| options.name | integer | Идентификатор модификации |
| options.options | integer |  |
| options.options.name | integer | Наименование |
| options.options.subnumber_id | integer | Идентификатор страницы с номером |
| positions | array | Номерные позиции |
| positions.index | integer | Порядковый номер |
| positions.number | string | Номер детали |
| positions.replacement | string | Замены |
| positions.name | string | Наименованин |
| positions.additional_information | string | Дополнительная информация |
| positions.coordinates | array | Координаты |
| positions.coordinates.top | object | Верхняя левая точка |
| positions.coordinates.top.x | integer | Верхняя левая точка x |
| positions.coordinates.top.y | integer | Верхняя левая точка y |
| positions.coordinates.bottom | object | Нижняя правая точка |
| positions.coordinates.bottom.x | integer | Нижняя правая точка x |
| positions.coordinates.bottom.y | integer | Нижняя правая точка y |


### Значения breadcrumbs

| Имя | Тип | Описание |
| :---- | :------: | :--------------- |
| name | string | Имя хлебной крошки |
| url | string | адрес текущей хлебной крошки |