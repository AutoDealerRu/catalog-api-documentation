# Модели

## `GET /:mark`

Возвращает объект с двумя массивами (models, breadcrumbs)

### Пример запроса

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/CARS_FOREIGN/SSANGYONG
```

### Пример ответа

```json
{
  "models": [
      ...
      ,{
          "name": "Actyon",
          "short_name": 389410638,
          "image": "https://212709.selcdn.ru/autocatalog-online/ssangyong/models/389410638.jpg",
          "type": "CARS_FOREIGN"
       },
      ...
  ],
  "breadcrumbs": [
      ...
      ,{
          "name": "SsangYong",
          "url": "SSANGYONG"
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


### Значения breadcrumbs

| Имя | Тип | Описание |
| :---- | :------: | :--------------- |
| name | string | Имя хлебной крошки |
| url | string | адрес текущей хлебной крошки |


## `GET /:mark/:short_name`

Для перехода к списку модификаций нужно выбрать модель и передать ее идентификатор (short_name) в GET параметры