# Детали для групп сервиса (numbers)

## `GET /:type/:mark/:country_short_name/:model/:year/:catalog_code/:dir/service/:service/:subservice`

Возвращает объект с массивами numbers, breadcrumbs и объектом subservice

| Конечная точка | Описание |
| :---- | :--------------- |
| GET /CARS_FOREIGN/AUDI/RA/A1/2014/708/R/service/100/CCA | Тормозные жидкости для Audi A1 |

### Пример запроса

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/CARS_FOREIGN/AUDI/RA/A1/2014/708/R/service/100/CCA
```

### Пример ответа

```json
{
    "breadcrumbs": [
        ...
        {
           "name": "Детали для устан. на сервисе",
           "url": 100
        },
    ],
    "subservice": {
        "mark": "AUDI",
        "subservice": "CCA",
        "name": "Тормозные жидкости"
    },
    "numbers": [
        {
            "mark": "AUDI",
            "catalog_code": 149,
            "dir": "R",
            "group": "6",
            "subservice": "CCA",
            "number": "B  000600A1",
            "amount": "X",
            "pr_number": "",
            "name": "Тормозная жидкость",
            "note": "0,25 л.",
            "model_info": "",
            "img": "http://auto2d.com/img/etka/Tnrpics/B__000600A1.jpg",
            "number_formatted": "B 0 006 00A 1"
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

### Значения subservice

| Имя точка | Тип | Описание |
| :---- | :------: | :--------------- |
| mark | string  | Название марки (AUDI, SEAT, SKODA или VOLKSWAGEN) |
| subservice | string  | Код подгруппы сервиса |
| name | string  | Название подгруппы сервиса |

### Значения numbers

| Имя точка | Тип | Описание |
| :---- | :------: | :--------------- |
| mark | string  | Название марки (AUDI, SEAT, SKODA или VOLKSWAGEN) |
| dir | string | Да | Директория |
| catalog_code | integer | Да | Код каталога |
| group | string | Да | Код группы |
| subservice | string  | Код подгруппы сервиса |
| number | string  | Номер детали |
| number_formatted | string  | Форматированный номер детали |
| name | string  | Название детали |
| note | string  | Примечание |
| model_info | string  | Данные по модели |
| amount | String  | Количество |
| pr_number | String  | Ввод данных по модели |
| img | String  | Картинка |