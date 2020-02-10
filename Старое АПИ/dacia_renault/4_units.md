# Сборочные узлы

## `GET /:mark/:model/:modification/:category`

Возвращает объект с объектом unit и массивом breadcrumbs

### Пример запроса

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/CARS_FOREIGN/RENAULT/61/3348/10042
```

### Пример ответа

```json
{
  "unit": {
    "image": "https://212709.selcdn.ru/autocatalog-online/renault/eclate/1292M.png",
    "groups": [
      {
        "index": 10,
        "name": "10 Двигатель",
        "coordinates": [
          {
            "bottom": {
              "x": 204,
              "y": 794
            },
            "top": {
              "x": 184,
              "y": 774
            }
          }
        ],
        "subgroups": [
          {
            "name": "Двигатель в сборе",
            "image": "https://212709.selcdn.ru/autocatalog-online/renault/vignette/10A.png",
            "short_name": 592624
          },
          {
            "name": "Уплотнения двигателя",
            "image": "https://212709.selcdn.ru/autocatalog-online/renault/vignette/10B.png",
            "short_name": 592625
          },
          ...
        ]
      },
      ...
    ],
    "mark_short_name": "RENAULT",
    "model_short_name": 61,
    "modification_short_name": 3348,
    "category_short_name": 10042
  },
  "breadcrumbs": [
    ...
    ,{
      "name": "Механические узлы",
      "url": "10042"
    }
  ]
}
```

### Значения

| Имя | Тип | Описание |
| :---- | :------: | :--------------- |
| unit.image | string | Ссылка на изображение |
| unit.groups | array | Группы деталей |
| unit.groups.index | integer | Порядковый номер |
| unit.groups.name | string | Наименование |
| unit.groups.coordinates | object | Координаты |
| unit.groups.coordinates.bottom | object | Нижняя правая точка |
| unit.groups.coordinates.bottom.x | integer | Нижняя правая точка x |
| unit.groups.coordinates.bottom.y | integer | Нижняя правая точка y |
| unit.groups.coordinates.top | object | Верхняя левая точка |
| unit.groups.coordinates.top.x | integer | Верхняя левая точка x |
| unit.groups.coordinates.top.y | integer | Верхняя левая точка y |
| unit.groups.subgroups | array | Подгруппы деталей |
| unit.groups.subgroups.name | string | Наименование |
| unit.groups.subgroups.image | string | Ссылка на изображение |
| unit.groups.subgroups.short_name | integer | Идентификатор подгруппы |
| unit.mark_short_name | string | Идентификатор категории |
| unit.model_short_name | integer | Идентификатор марки |
| unit.modification_short_name | integer | Идентификатор модификации |
| unit.category_short_name | integer | Идентификатор категории |


### Значения breadcrumbs

| Имя | Тип | Описание |
| :---- | :------: | :--------------- |
| name | string | Имя хлебной крошки |
| url | string | адрес текущей хлебной крошки |


## `GET /:mark/:model/:modification/:short_name/:unit.groups.subgroups.short_name`

Для перехода к списку номеров узлов нужно выбрать подгруппу и передать ее идентификатор (short_name) в GET параметры