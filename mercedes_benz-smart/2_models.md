# Страны (countries)

## `GET /:type/:mark`

Возвращает объект с двумя массивами countries и breadcrumbs

| Конечная точка | Описание |
| :---- | :--------------- |
| GET /CARS_FOREIGN/MERCEDES_BENZ | Страны и аггрегаты марки Mercedes Benz (Легковых иномарок) |
| GET /BUS/MERCEDES_BENZ | Страны и аггрегаты марки Mercedes Benz (Автобусы) |
| GET /SPECIAL_TECH_FOREIGN/MERCEDES_BENZ | Страны и аггрегаты марки Mercedes Benz (Спецтехника ) |
| GET /TRUCKS_FOREIGN/MERCEDES_BENZ | Страны и аггрегаты марки Mercedes Benz (Грузовики) |
| GET /CARS_FOREIGN/SMART | Страны и аггрегаты марки Smart (Легковых иномарок) |

### Пример запроса

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/CARS_FOREIGN/MERCEDES_BENZ
```

### Пример ответа

```json
{
    "countries": [
        {
            "type": "CARS_FOREIGN",
            "mark": "MERCEDES_BENZ",
            "short": "EU",
            "name": "Европа",
            "current": false,
            "aggregations": [
                {
                    "short": "GA",
                    "name": "Автоматическая кп",
                    "image": "http://212709.selcdn.ru/autocatalog-online/mercedes/aggregate/akpp.png"
                },
                ...
            ],
        },
        ...
    ],
    "breadcrumbs": [
        ...
        ,{
          "name": "MERCEDES BENZ",
          "url": "MERCEDES_BENZ"
        }
    ]
}
```

### Значения countries

| Имя точка | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| type | string | Да | Тип машины (всегда CARS_FOREIGN) |
| mark | string | Да | Название марки (NISSAN или INFINITI) |
| short | string | Да | Сокращение страны (например: AR / GL ) |
| name | string | - | Полное название страны |
| current | boolean | - | Текущая страна (Да / Нет) |
| aggregations | array of objects | - | Список агрегатов страны |
| aggregations[..].short | string | Да | Сокращение агрегата |
| aggregations[..].name | string | - | Название агрегата |
| aggregations[..].short | string | - | Изображение агрегата |

### Значения breadcrumbs

| Имя точка | Тип | Описание |
| :---- | :------: | :--------------- |
| name | string | Имя хлебной крошки |
| url | string | адрес текущей хлебной крошки |


## `GET /:type/:mark/:country/:aggregation`

Для перехода к списку моделей нужно выбрать страну (short), аггрегат (aggregations[..].short) и передать их в GET параметры