# Группы

## `GET /:mark/:model`

Возвращает объект с двумя массивами (groups, breadcrumbs)

### Пример запроса

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/CARS_FOREIGN/SSANGYONG/389410638
```

### Пример ответа

```json
{
  "groups": [
      ...
      ,{
          "name": "Body",
          "short_name": 1633727457,
          "model_short_name": 389410638,
          "subgroups": [
              {
                  "short_name": 1888337408,
                  "name": "BODY MOUNTING"
              },
              ...
          ],
          "type": "CARS_FOREIGN",
          "mark_short_name": "SSANGYONG"
        },
      ...
  ],
  "breadcrumbs": [
      ...
      ,{
          "name": "Actyon",
          "url": "389410638"
      }
  ]
}
```

### Значения groups

| Имя | Тип | Описание |
| :---- | :------: | :--------------- |
| name | string | Наименование группы |
| short_name | integer | Идентификатор группы |
| subgroups | array | Подгруппы |
| subgroups.short_name | integer | Идентификатор подгруппы |
| subgroups.name | array | Название подгруппы |
| type | string | Тип транспортного средства |
| mark_short_name | string | Идентификатор марки |



### Значения breadcrumbs

| Имя | Тип | Описание |
| :---- | :------: | :--------------- |
| name | string | Имя хлебной крошки |
| url | string | адрес текущей хлебной крошки |


## `GET /:mark/:model/:short_name`

Для перехода к списку номеров деталей нужно выбрать подгруппы и передать ее идентификатор (short_name) в GET параметры