# Страны (countries)

## `GET /:mark`

Возвращает объект с двумя массивами countries и breadcrumbs

| Конечная точка | Описание |
| :---- | :--------------- |
| GET /BUS/KIA | Страны марки KIA Автобусов |
| GET /CARS_FOREIGN/KIA | Страны марки KIA Легковых иномарок |
| GET /TRUCKS_FOREIGN/KIA | Страны марки KIA Грузовых иномарок|
| GET /BUS/HYUNDAI | Страны марки HYUNDAI Автобусов |
| GET /CARS_FOREIGN/HYUNDAI | Страны марки HYUNDAI Легковых иномарок |
| GET /TRUCKS_FOREIGN/HYUNDAI | Страны марки HYUNDAI Грузовых иномарок|

### Пример запроса

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/CARS_FOREIGN/KIA
```

### Пример ответа

```json
{
    "countries": [
        {
            "type": "CARS_FOREIGN",
            "mark": "KIA",
            "country_short": "AUS",
            "full_name": "Австралия"
        },
        ...
    ],
    "breadcrumbs": [
        ...
        ,{
            "name": "KIA",
            "url": "KIA"
        }
    ]
}
```

### Значения countries

| Имя точка | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| type | string | - | Тип кузова |
| mark | string | - | Название марки (KIA или HYUNDAI) |
| country_short | string | Да | Сокращение страны (например: AUS / MES ) |
| full_name | string | - | Полное название страны |

### Значения breadcrumbs

| Имя точка | Тип | Описание |
| :---- | :------: | :--------------- |
| name | string | Имя хлебной крошки |
| url | string | адрес текущей хлебной крошки |


## `GET /:mark/:country_short`

Для перехода к списку семейств нужно выбрать страну и передать ее сокращение (country_short) в GET параметры