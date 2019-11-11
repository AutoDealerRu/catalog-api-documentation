# Номера (numbers)

## `GET /:type/:mark/:model/:modification/:group/:subgroup[?criteria=...]`

Возвращает объект содержащий model, modification, group, breadcrumbs, image, labels, numbers

| Конечная точка | Описание |
| :---- | :--------------- |
| GET /CARS_FOREIGN/mitsubishi/d044189982d7063dee143c0a7264f1ee/817904ab9b87057e1baa7033cdf94530/MfCfmoAxMQ/MvCfmoAxMfCfmoExMzAsMA | Номера Mitsubishi 3000GT |

### Пример запроса

```bash
curl -H 'Authorization: <token>' -X GET https://acat.online/api/catalogs/CARS_FOREIGN/mitsubishi/d044189982d7063dee143c0a7264f1ee/817904ab9b87057e1baa7033cdf94530/MfCfmoAxMQ/MvCfmoAxMfCfmoExMzAsMA
```

### Пример ответа

```json
{
    "breadcrumbs": [
            ...,
        {
            "name": "Блок цилиндров",
            "url": "MvCfmoAxMfCfmoExMzAsMA?groupId=MfCfmoAxMQ"
        }
    ],
    "model": {
        "img": "//img.parts-catalogs.com/models/mitsubishi/3000GT.jpg",
        "name": "3000GT",
        "id": "d044189982d7063dee143c0a7264f1ee"
    },
    "modification": {
        "model": {
            "name": "3000GT",
            "id": "d044189982d7063dee143c0a7264f1ee"
        },
        "params": [],
        "filters": null,
        "transmission": {
            "type": null,
            "name": null
        },
        "engine": null,
        "bodyType": null,
        "steeringId": null,
        "steering": null,
        "year": "1990",
        "region": "Европа",
        "description": "PREMIUM LINE(DOHC),5FM/T             CAL\r\n3000/2WD\r\nModification: Z11A\r\nClassification: MNPML7M\r\nProduction: 01.04.1990 - 03.06.2000",
        "name": "3000GT(EUR)",
        "catalogId": "mitsubishi",
        "id": "817904ab9b87057e1baa7033cdf94530"
    },
    "group": {
        "description": "OIL LEVEL GAUGE",
        "img": "//img.parts-catalogs.com/r/250x250/mitsubishi_2019_03/euro/111/111_130500112T.png",
        "name": "Блок цилиндров",
        "hasParts": true,
        "hasSubgroups": false,
        "parentId": "MfCfmoAxMQ",
        "id": "MvCfmoAxMfCfmoExMzAsMA"
    },
    "labels": [
        {
            "coordinate": {
                "bottom": {
                    "y": 393,
                    "x": 122
                },
                "top": {
                    "y": 375,
                    "x": 40
                }
            },
            "number": "04999"
        },
        ...
    ],
    "image": "//img.parts-catalogs.com/mitsubishi_2019_03/euro/111/111_130500112T.png",
    "numbers": [
        {
            "name": "BLOCK ASSY,CYLINDER",
            "description": null,
            "positionNumber": null,
            "number": "01300A",
            "parts": [
                {
                    "id": "MD160281",
                    "name": null,
                    "number": "MD160281",
                    "positionNumber": "01300A",
                    "description": "Применяемость: \n   01.04.1990 - 03.09.1992\n   Все автомобили\nКол-во деталей: 1",
                    "notice": ""
                },
                ...
            ]
        }
    ]
}
```

### Значения labels

| Имя точка | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| number | string | - | Номер детали |
| coordinate | Object | - | Координата |
| coordinate.top | Object | - | Верхняя координата |
| coordinate.top.x | Integer | - | Верхняя координата Х |
| coordinate.top.y | Integer | - | Верхняя координата Y |
| coordinate.bottom | Object | - | Нижняя координата |
| coordinate.bottom.x | Integer | - | Нижняя координата Х |
| coordinate.bottom.y | Integer | - | Нижняя координата Y |

### Значения numbers

| Имя точка | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| name | string | - | Название группы (/детали) |
| description | string | - | Описание группы |
| positionNumber | string | - | Номер позиции |
| number | string | - | Номер группы |
| parts | object[] | - | Список номеров |
| parts[..].id | string | - | Номер |
| parts[..].name | string/null | - | Название |
| parts[..].number | string | - | Номер |
| parts[..].positionNumber | string | - | Номер группы |
| parts[..].description | string | - | Описание |
| parts[..].notice | string | - | Примечание |

### Значения group

| Имя точка | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| id | string | Да | Идентификатор модели |
| name | string | - | Название группы/подгруппы |
| img | string/null | - | Ссылка на изображение |

### Значения model

| Имя точка | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| id | string | - | Идентификатор модели |
| name | string | - | Имя модели |
| img | string | - | Ссылка на изображение |

### Значения modification

| Имя точка | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| id | string | - | Идентификатор модификации |
| name | string | - | Название модификации |
| model.name | string | - | Имя модели |
| model.id | string | - | ID модели |
| transmission.name | string/null | - | Имя трансмиссии |
| transmission.type | string/null | - | Тип трансмиссии |
| engine | string/null | - | Двигатель |
| bodyType | string/null | - | Тип кузова |
| steering | string/null | - | Рулевое управление |
| year | string/null | - | Год выпуска |
| region | string/null | - | Регион |
| description | string/null | - | Описание |

### Значения breadcrumbs

| Имя точка | Тип | Описание |
| :---- | :------: | :--------------- |
| name | string | Имя хлебной крошки |
| url | string | адрес текущей хлебной крошки |