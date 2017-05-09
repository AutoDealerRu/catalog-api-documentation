# Категории

## `GET /:mark/:model/:modification`

Возвращает объект с двумя массивами (categories, breadcrumbs)

### Пример запроса

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/CARS_FOREIGN/RENAULT/61/3348
```

### Пример ответа

```json
{
  "categories": [
    {
      "name": "Механические узлы",
      "image": "https://212709.selcdn.ru/autocatalog-online/renault/eclate/1292M.jpg",
      "short_name": 10042,
      "mark_short_name": "RENAULT",
      "model_short_name": 61,
      "modification_short_name": 3348
    },
    {
      "name": "Кузов",
      "image": "https://212709.selcdn.ru/autocatalog-online/renault/eclate/1292C.jpg",
      "short_name": 10043,
      "mark_short_name": "RENAULT",
      "model_short_name": 61,
      "modification_short_name": 3348
    },
    ...
  ],
  "breadcrumbs": [
    ...
    ,{
      "name": "BJ03",
      "url": "3348"
    }
  ]
}
```

### Значения categories

| Имя | Тип | Описание |
| :---- | :------: | :--------------- |
| name | string | Наименование категории |
| image | string | Ссылка на изображение |
| short_name | integer | Идентификатор категории |
| mark_short_name | string | Идентификатор марки |
| model_short_name | integer | Идентификатор модели |
| modification_short_name | integer | Идентификатор модификации |

### Значения breadcrumbs

| Имя | Тип | Описание |
| :---- | :------: | :--------------- |
| name | string | Имя хлебной крошки |
| url | string | адрес текущей хлебной крошки |


## `GET /:mark/:model/:modification/:short_name`

Для перехода к списку сборочных узлов нужно выбрать категорию и передать ее идентификатор (short_name) в GET параметры