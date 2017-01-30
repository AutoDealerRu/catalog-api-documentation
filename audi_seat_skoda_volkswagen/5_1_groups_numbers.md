# Детали (numbers)

## `GET /:type/:mark/:country_short_name/:model/:year/:catalog_code/:dir/group/:group/:subgroup/:detail`

Возвращает объект с массивами numbers, breadcrumbs и объектом subgroup

| Конечная точка | Описание |
| :---- | :--------------- |
| GET /CARS_FOREIGN/AUDI/RDW/A100/1994/149/R/group/1/100/100010 | Блок цил. с коленвалом, порш- нями, мас. нас. и мас. подд для Audi A1 |

### Пример запроса

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/CARS_FOREIGN/AUDI/RDW/A100/1994/149/R/group/1/100/100010
```

### Пример ответа

```json
{
    "breadcrumbs": [
        ...
        {
            "name": "Блок цил. с коленвалом, порш-\r\nнями, мас. нас. и мас. подд.",
            "url": "100"
        }
    ],
    "subgroup": {
        "mark": "AUDI",
        "dir": "R",
        "catalog_code": 149,
        "group": "1",
        "subgroup": "100",
        "detail": 100010,
        "name": "Блок цил. с коленвалом, порш-\r\nнями, мас. нас. и мас. подд.",
        "options": "",
        "image": "https://acat.online/api/catalogs/CARS_FOREIGN/AUDI/RDW/A100/1994/149/R/group/1/100/100010/image"
    },
    "numbers": [
        {
            "mark": "AUDI",
            "catalog_code": 149,
            "dir": "R",
            "group": "1",
            "subgroup": "100",
            "detail": 100010,
            "number": "048100103C",
            "amount": "1,1",
            "name": "Блок цилиндров в сборе для механической КП использовать с:",
            "note": "74KW 2,0 л.   056 105 313 C",
            "model_info": "AAE",
            "number_formatted": "048 100 103 C",
            "coordinate": [
                {
                    "top": {
                        "x": 1367,
                        "y": 1055,
                    },
                    "bottom": {
                        "x": 1438,
                        "y": 1124,
                    }
                },
                ...
            ]
        },
        ...
    ]

}
```

### Значения breadcrumbs

| Имя точка | Тип | Описание |
| :---- | :------: | :--------------- |
| name | string | Имя хлебной крошки |
| url | string | адрес текущей хлебной крошки |

### Значения subgroup

| Имя точка | Тип | Описание |
| :---- | :------: | :--------------- |
| mark | string | Название марки (AUDI, SEAT, SKODA или VOLKSWAGEN) |
| catalog_code | integer | Код каталога |
| dir | string | Директория (используется в get-параметрах) |
| group | string | Код группы |
| subgroup | string | Код подгруппы |
| detail | string | Код группы деталей |
| name | string | Название подгруппы |
| options | string | Опции |
| image | string | Иллюстрация |

### Значения numbers

| Имя точка | Тип | Описание |
| :---- | :------: | :--------------- |
| mark | string  | Название марки (AUDI, SEAT, SKODA или VOLKSWAGEN) |
| dir | string | Да | Директория |
| catalog_code | integer | Да | Код каталога |
| group | string | Да | Код группы |
| subgroup | string | Код подгруппы |
| detail | integer  | Код группы деталей |
| number | string  | Номер детали |
| number_formatted | string  | Форматированный номер детали |
| name | string  | Название детали |
| note | string  | Примечание |
| model_info | string  | Данные по модели |
| amount | String  | Количество |
| coordinate[] | Object | Координаты |
| coordinate[].top | Object |  Верхняя координата |
| coordinate[].top.x | Integer | Верхняя координата Х |
| coordinate[].top.y | Integer | Верхняя координата Y |
| coordinate[].bottom | Object | Нижняя координата |
| coordinate[].bottom.x | Integer | Нижняя координата Х |
| coordinate[].bottom.y | Integer |  Нижняя координата Y |