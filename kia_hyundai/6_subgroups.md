# Подгруппы (subgroups)

## `GET /:type/:mark/:country_short/:family/:model/:modification/:group`

Возвращает объект с двумя массивами subgroups и breadcrumbs

### Примеры

| Конечная точка | Описание |
| :---- | :--------------- |
| GET /CARS_FOREIGN/KIA/EUR/CARENS/EURK1D006A/BKWDS65/AC | Подгруппы для CARENS 06: -OCT.2006 (2006-2006) BKWDS65 Аксессуары |

### Пример запроса

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/CARS_FOREIGN/KIA/EUR/CARENS/EURK1D006A/BKWDS65/AC
```

### Пример ответа

```json
{
    "subgroups": [
        {
           "type": "CARS_FOREIGN",
           "mark": "KIA",
           "country_short": "EUR",
           "family": "CARENS",
           "model": "EURK1D006A",
           "modification": "BKWDS65",
           "group": "AC",
           "subgroup": "AC004457EU",
           "name": "AC-001-EU  TOW BAR",
           "image": "KIA/Thumb/EURK1D00/AC004457EU.png"
        },
        ...
    ],
    "breadcrumbs": [
        ...
        ,{
            "name": "Аксессуары",
            "url": "AC"
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
| group | string | - | Сокращение группы |
| subgroup | string | Да | Сокращение подгруппы |
| name | string | - | Название группы |
| image | string | - | Путь до изображения группы |

### Значения breadcrumbs

| Имя точка | Тип | Описание |
| :---- | :------: | :--------------- |
| name | string | Имя хлебной крошки |
| url | string | адрес текущей хлебной крошки |


## `GET /:type/:mark/:country_short/:family/:model/:modification/:group/:subgroup`

Для перехода к списку номеров нужно выбрать подгруппу и передать ее сокращение (subgroup) в GET параметры