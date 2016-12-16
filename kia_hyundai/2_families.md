# Семейства (families)

## `GET /:mark/:country_short`

Возвращает объект с двумя массивами families и breadcrumbs

### Примеры

| Конечная точка | Описание |
| :---- | :--------------- |
| GET /KIA/EUR | Семейства марки KIA Европа |
| GET /HYUNDAI/USA | Семейства марки HYUNDAI США |

### Пример запроса

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/CARS_FOREIGN/KIA/EUR
```

### Пример ответа

```json
{
    "families": [
        {
           "type": "CARS_FOREIGN",
           "mark": "KIA",
           "country_short": "EUR",
           "family": "AVELLA"
        },
        ...
    ],
    "breadcrumbs": [
        ...
        ,{
            "name": "Европа",
            "url": "EUR"
        }
    ]
}
```

### Значения families

| Имя точка | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| type | string | - | Тип кузова |
| mark | string | - | Название марки (KIA или HYUNDAI) |
| country_short | string | - | Сокращение страны (например: AUS / MES ) |
| family | string | Да | Семейство (одна модель может относится к нескольким семействам) |

### Значения breadcrumbs

| Имя точка | Тип | Описание |
| :---- | :------: | :--------------- |
| name | string | Имя хлебной крошки |
| url | string | адрес текущей хлебной крошки |


## `GET /:mark/:country_short/:family`

Для перехода к списку моделей нужно выбрать Семейство (family) и передать его в GET параметры