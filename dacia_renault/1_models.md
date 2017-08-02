# Модели

## `GET /:mark`

Возвращает объект с двумя массивами (models, breadcrumbs)

### Пример запроса

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/CARS_FOREIGN/RENAULT
```

### Пример ответа

```json
{
  "models": [
      ...
      ,{
          "type": "CARS_FOREIGN",
          "name": "Duster",
          "short_name": 12,
          "mark_short_name": "RENAULT"
      },
      ...
  ],
  "breadcrumbs": [
      ...
      ,{
          "name": "Renault",
          "url": "RENAULT"
      }
  ]
}
```

### Значения models

| Имя | Тип | Описание |
| :---- | :------: | :--------------- |
| type | string | Тип транспортного средства |
| name | string | Наименование модели |
| short_name | integer | Идентификатор модели |
| mark_short_name | string | Идентификатор марки |


### Значения breadcrumbs

| Имя | Тип | Описание |
| :---- | :------: | :--------------- |
| name | string | Имя хлебной крошки |
| url | string | адрес текущей хлебной крошки |


## `GET /:mark/:short_name`

Для перехода к списку модификаций нужно выбрать модель и передать ее идентификатор (short_name) в GET параметры