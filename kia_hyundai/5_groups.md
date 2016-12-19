# Группы (groups)

## `GET /:type/:mark/:country_short/:family/:model/:modification`

Возвращает объект с двумя массивами groups и breadcrumbs

### Примеры

| Конечная точка | Описание |
| :---- | :--------------- |
| GET /CARS_FOREIGN/KIA/EUR/CARENS/EURK1D006A/BKWDS65 | Группы для CARENS 06: -OCT.2006 (2006-2006) BKWDS65 |

### Пример запроса

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/CARS_FOREIGN/KIA/EUR/CARENS/EURK1D006A/BKWDS65
```

### Пример ответа

```json
{
    "groups": [
        {
           "type": "CARS_FOREIGN",
           "mark": "KIA",
           "country_short": "EUR",
           "family": "CARENS",
           "model": "EURK1D006A",
           "modification": "BKWDS65",
           "group": "AC",
           "name": "Аксессуары",
           "image": "KIA/Maj/AC.png"
        },
        ...
    ],
    "breadcrumbs": [
        ...
        ,{
            "name": "BKWDS65",
            "url": "BKWDS65"
        }
    ]
}
```

### Значения modifications

| Имя точка | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| type | string | - | Тип кузова |
| mark | string | - | Название марки (KIA или HYUNDAI) |
| country_short | string | - | Сокращение страны (например: AUS / MES ) |
| family | string | - | Семейство (одна модель может относится к нескольким семействам) |
| model | string | - | Название модели (например ATLAS) |
| modification | string | - | Номер модификации |
| group | string | Да | Сокращение группы |
| name | string | - | Название группы |
| image | string | - | Путь до изображения группы |

### Значения breadcrumbs

| Имя точка | Тип | Описание |
| :---- | :------: | :--------------- |
| name | string | Имя хлебной крошки |
| url | string | адрес текущей хлебной крошки |


## `GET /:type/:mark/:country_short/:family/:model/:modification/:group`

Для перехода к списку подгрупп нужно выбрать группу и передать ее сокращение (group) в GET параметры