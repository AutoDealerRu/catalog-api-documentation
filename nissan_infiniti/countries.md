# Страны (countries)

## `GET /:mark`

Возвращает объект с двумя массивами countries и breadcrumbs

| Конечная точка | Описание |
| :---- | :--------------- |
| [GET /NISSAN] | Список доступный стран Nissan |
| [GET /INFINITI] | Список доступный стран Infiniti |

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
        {
        "name": "Каталог",
        "url": "/catalogs"
        },
        ...
    ]
}
```

### Значения countries

| Имя точка | Тип | Описание |
| :---- | :------: | :--------------- |
| type | string | Тип машины (в данном каталоге только CARS_FOREIGN - легковые иномарки) |
| mark | string | Название марки (NISSAN или INFINITI) |
| country_short_name | string | Сокращение страны (например: AR / GL ) |
| full_name | string | Полное название страны |

### Значения breadcrumbs

| Имя точка | Тип | Описание |
| :---- | :------: | :--------------- |
| name | string | Имя хлебной крошки |
| url | string | адрес текущей хлебной крошки |


## `GET /:mark/:country_short_name`

Для перехода к списку моделей нужно выбрать одну из стран и передать ее сокращение (country_short_name)