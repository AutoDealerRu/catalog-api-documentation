# Группы (groups)

## `GET /:type/:mark/:country/:aggregation/:model/:catalog`

Возвращает объект с двумя массивами models и breadcrumbs

| Конечная точка | Описание |
| :---- | :--------------- |
| GET /CARS_FOREIGN/MERCEDES_BENZ/EU/FG/201023/15C | Модели марки MERCEDES BENZ Европа Шасси |
| GET /CARS_FOREIGN/SMART/SM/M/122950/60H | Модели марки Smart Двигатель |

### Пример запроса

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/CARS_FOREIGN/MERCEDES_BENZ/EU/FG/201023/15C
```

### Пример ответа

```json
{
    "groups": [
        ...
        ,{
            "type": "CARS_FOREIGN",
            "mark": "MERCEDES_BENZ",
            "country": "EU",
            "aggregation": "FG",
            "model": "201023",
            "catalog": "15C",
            "short": "26",
            "name": "ПЕРЕКЛЮЧЕНИЕ",
            "subgroups": [
                ...
                ,{
                    "short": "060",
                    "name": "FLOOR SHIFT,AUTOMATIC TRANSMISSION"
                },{
                    "short": "11347",
                    "name": "STEERING WHEEL & GEARSHIFT LEVER W/LEATHER COVER (FOR TYPE 124, SEE STANDARD MICROFICHE)",
                    "codes": [
                        "280",
                        "281",
                        "289"
                    ],
                    "sa_subgroup": true,
                    "items": [
                        {
                            "sa_subgroup_id": 11347,
                            "subgroup_name": "STEERING WHEEL & GEARSHIFT LEVER W/LEATHER COVER (FOR TYPE 124, SEE STANDARD MIC",
                            "subgroup_id": "001",
                            "stroke_id": "11",
                            "footnotes": null,
                            "consas": null,
                            "description": "GEARSHIFT LEVER USED FOR MANUAL FIVE-SPEEDTRANSMISSION, SEE SA 11 245",
                        },
                        ...
                    ]
                },
                ...
            ]
        },
        ...
    ],
    "breadcrumbs": [
        ...
        ,{
            "name": "201.023",
            "url": "201023/15C"
        }
    ]
}
```

### Значения groups

| Имя точка | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| type | string | Да | Тип машины (всегда CARS_FOREIGN) |
| mark | string | Да | Название марки (NISSAN или INFINITI) |
| country | string | Да | Сокращение страны (например: EU / US ) |
| aggregation | string | Да | Сокращение агрегата (например: FG / M ) |
| model | string | Да | Сокращение модели |
| catalog | string | Да | Код каталога |
| model_formatted | string | - | Идентификатор модели |
| modification | string | - | Информация о модификации |
| name | string | - | Имя модели |
| from_date | null / Date | - | Дата начала производства |
| to_date | null / Date | - | Дата окончания производства |
| remark | null / String | - | Дополнительная информация |

### Значения breadcrumbs

| Имя точка | Тип | Описание |
| :---- | :------: | :--------------- |
| name | string | Имя хлебной крошки |
| url | string | адрес текущей хлебной крошки |


## `GET /:type/:mark/:country/:aggregation/:model/:catalog`

Для перехода к списку моделей нужно выбрать модель (model) и каталог (catalog) и передать их в GET параметры