# Информация по номеру (number_information)

## `GET /:type/:mark/:mark_short_name/:model_id/:modification_id/:group_id/:provider_id/:number/:article_id`

Возвращает объект с двумя массивам numbers и breadcrumbs

| Конечная точка | Описание |
| :---- | :--------------- |
| GET /CARS_FOREIGN/AFTERMARKET/AC/4211/12428/12096/11353/XLS011/129385604 | Информация AC ACE 4.6 Масла XLS011 (Масло осевого редуктора)|

### Пример запроса

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/CARS_FOREIGN/AFTERMARKET/AC/4211/12428/12096/11353/XLS011/129385604
```

### Пример ответа

```json
{
    "number": [
        
        ...
    ],
    "breadcrumbs": [
        ...
        ,{
            "name": "Масла",
            "url": "12096"
        }
    ]
}
```

### Значения groups

| Имя точка | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| type | string | - | Тип кузова |
| mark | string | - | Название каталога (всегда будет AFTERMARKET) |
| mark_short_name | string | - | Сокращенное название марки |
| model_id | integer | - | Идентифкационный номер модели |
| modification_id | integer | - | Идентифкационный номер модификации |
| group_id | integer | - | Идентифкационный номер группы |
| number | string | Да | Номер |
| name | string | - | Название детали |
| article_id | integer | Да | ID артикула |
| provider | object | - | Производитель |
| provider.id | integer | Да | ID производителя |
| provider.name | string | - | Название производителя |
| provider.image | string | - | Путь до изображения производителя |

### Значения breadcrumbs

| Имя точка | Тип | Описание |
| :---- | :------: | :--------------- |
| name | string | Имя хлебной крошки |
| url | string | Адрес текущей хлебной крошки |