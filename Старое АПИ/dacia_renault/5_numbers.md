# Номера

## `GET /:mark/:model/:modification/:category/:subgroup`

### Пример запроса

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/CARS_FOREIGN/RENAULT/61/3348/10042
```

### Пример ответа

```json
{
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
  "image": "https://acat.online/api/catalogs/CARS_FOREIGN/RENAULT/61/3348/10042/image",
  "related": [
    {
      "name": "N400112",
      "subnumber_id": "58d87adf28798c02743e9181"
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
        ...
      ]
    },
    ...
  ],
  "positions": [
    {
      "index": 1,
      "number": "600503272R",
      "replacement": "",
      "name": "",
      "additional_information": "Технические и законодательные требования страны = TLARGE",
      "coordinates": [
        {
          "bottom": {
            "x": 472,
            "y": 26
          },
          "top": {
            "x": 454,
            "y": 8
          }
        }
      ]
    },
    ...
  ]
}
```

### Значения

| Имя | Тип | Описание |
| :---- | :------: | :--------------- |
| image | string | Ссылка на изображение |
| mark_short_name | string | Идентификатор марки |
| model_short_name | integer | Идентификатор модели |
| modification_short_name | integer | Идентификатор модификации |
| category_short_name | integer | Идентификатор категории |
| subgroup_short_name | integer | Идентификатор подгруппы |
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


## `GET /:mark/:model/:modification/:category/:subgroup/:subnumber_id`

Для перехода к дополнительным номерам нужно выбрать related или option subnumber_id и передать его в GET параметры