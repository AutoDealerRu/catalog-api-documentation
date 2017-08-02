# Модификации

## `GET /:mark/:model`

Возвращает объект с двумя массивами (modifications, breadcrumbs)

### Пример запроса

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/CARS_FOREIGN/RENAULT/61
```

### Пример ответа

```json
{
  "modifications": [
    {
      "name": "BJ00",
      "mark_short_name": "RENAULT",
      "short_name": 3346,
      "model_short_name": 61
    },
    {
      "name": "BJ01",
      "mark_short_name": "RENAULT",
      "short_name": 3347,
      "model_short_name": 61
    },
    ...
  ],
  "breadcrumbs": [
    ...
    ,{
      "name": "Vel Satis",
      "url": "61"
    }
  ]
}
```

### Значения modifications

| Имя | Тип | Описание |
| :---- | :------: | :--------------- |
| name | string | Наименование модификации |
| mark_short_name | string | Идентификатор марки |
| short_name | integer | Идентификатор модификации |
| model_short_name | integer | Идентификатор модели |

### Значения breadcrumbs

| Имя | Тип | Описание |
| :---- | :------: | :--------------- |
| name | string | Имя хлебной крошки |
| url | string | адрес текущей хлебной крошки |


## `GET /:mark/:model/:short_name`

Для перехода к списку категорий нужно выбрать модификацию и передать ее идентификатор (short_name) в GET параметры