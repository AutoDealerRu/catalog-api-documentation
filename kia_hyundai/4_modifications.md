# Модификации (modifications)

## `GET /:type/:mark/:country_short/:family/:model`

Возвращает объект с двумя массивами modifications и breadcrumbs

### Примеры

| Конечная точка | Описание |
| :---- | :--------------- |
| GET /CARS_FOREIGN/KIA/EUR/CARENS/EURK1D006A | Модификации для CARENS 06: -OCT.2006 (2006-2006) |

### Пример запроса

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/CARS_FOREIGN/KIA/EUR/CARENS/EURK1D006A
```

### Пример ответа

```json
{
    "modifications": [
        {
           "type": "CARS_FOREIGN",
           "mark": "KIA",
           "model": "EURK1D006A",
           "modification": "BKWDS65",
           "from_date": "2006-06-01T00:00:00.000Z",
           "to_date": null,
           "body": "5 DR WAGON",
           "class": "MIDDLE GRADE",
           "engine_displacement": "2000 CC",
           "fuel": "MPI-DOHC",
           "transmission": "5 SPEED MT 2WD"
        },
        ...
    ],
    "breadcrumbs": [
        ...
        ,{
            "name": "CARENS 06: -OCT.2006 (2006-2006)",
            "url": "EURK1D006A"
        }
    ]
}
```

### Значения modifications

| Имя точка | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| type | string | Да | Тип кузова |
| mark | string | Да | Название марки (KIA или HYUNDAI) |
| country_short | string | Да | Сокращение страны (например: AUS / MES ) |
| family | string | Да | Семейство (одна модель может относится к нескольким семействам) |
| model | string | Да | Название модели (например ATLAS) |
| modification | string | Да | Номер модификации |
| from_date | null/Date | - | Дата производства "от" |
| to_date | null/Date | - | Дата производства "до" |
| body | string | - | Кузов |
| class | string | - | Кузов |
| engine_displacement | string | - | Объем двигателя |
| engine | string | - | Двигатель |
| fuel | string | - | Топливо |
| transmission | string | - | Трансмиссия |
| door_floor | string | - | door_floor |
| door_usage | string | - | door_usage |
| suspension | string | - | Подвеска |
| wheel_base | string | - | Колесная база |
| car_type | string | - | Тип мышины |

#### ВАЖНО! В списке параметров характеристики, что идут после дат у каждой модели свои.
#### Например: у одной модификации будет body & class, у другой может быть fuel & car_type

### Значения breadcrumbs

| Имя точка | Тип | Описание |
| :---- | :------: | :--------------- |
| name | string | Имя хлебной крошки |
| url | string | адрес текущей хлебной крошки |


## `GET /:type/:mark/:country_short/:family/:model/:modification`

Для перехода к списку групп нужно выбрать модификацию и передать ее сокращение (modification) в GET параметры