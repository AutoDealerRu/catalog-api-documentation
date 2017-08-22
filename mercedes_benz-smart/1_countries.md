# Страны (countries)

## `GET /:mark`

Возвращает объект с двумя массивами countries и breadcrumbs

| Конечная точка | Описание |
| :---- | :--------------- |
| GET /NISSAN | Страны марки Nissan |
| GET /INFINITI | Страны марки Infiniti |

### Пример запроса

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/CARS_FOREIGN/NISSAN
```

### Пример ответа

```json
{
    "countries": [
        {
            "type": "CARS_FOREIGN",
            "mark": "NISSAN",
            "country_short_name": "AR",
            "full_name": "Австралия"
        },
        ...
    ],
    "breadcrumbs": [
        ...
        ,{
            "name": "NISSAN",
            "url": "NISSAN"
        }
    ]
}
```

### Значения countries

| Имя точка | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| type | string | Да | Тип машины (всегда CARS_FOREIGN) |
| mark | string | Да | Название марки (NISSAN или INFINITI) |
| country_short_name | string | Да | Сокращение страны (например: AR / GL ) |
| full_name | string | - | Полное название страны |

### Значения breadcrumbs

| Имя точка | Тип | Описание |
| :---- | :------: | :--------------- |
| name | string | Имя хлебной крошки |
| url | string | адрес текущей хлебной крошки |


## `GET /:mark/:country_short_name`

Для перехода к списку моделей нужно выбрать страну и передать ее сокращение (country_short_name) в GET параметры