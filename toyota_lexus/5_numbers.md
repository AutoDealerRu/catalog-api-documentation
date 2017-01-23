# Номера деталей (numbers)

## `GET /:type/:mark_short_name/:country_short_name/:model_code/:sysopt/:complectation_code/:group/:illustration`

Возвращает объект с массивами numbers, breadcrumbs

### Примеры

| Конечная точка | Описание |
| :---- | :--------------- |
| GET /CARS_FOREIGN/TOYOTA/US/671440/LN51L-KRA/sysopt/001/0901/MT0887F | Список деталей US 4-RUNNER TRUCK комплектация LN51L-KRA группа STANDARD TOOL (Двигатель, топливная система и инструменты) |

### Пример запроса

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/CARS_FOREIGN/TOYOTA/US/671440/LN51L-KRA/sysopt/001/0901/MT0887F
```

### Пример ответа

```json
{
    "numbers": [
        {
            "sysopt": "sysopt",
            "model_code": "LN51L-KRA",
            "catalog_code": "671440",
            "mark_short_name": "TOYOTA",
            "type": "CARS_FOREIGN",
            "country_short_name": "US",
            "disk": "B1",
            "illustration_short_name": "MT0887F",
            "number": "09110",
            "related_group": "09110",
            "number_type": 3,
            "description": "JACK ASSY",
            "related_illustration_short_name": "",
            "coordinate": {
                "top": {
                    "x": 300,
                    "y": 35
                },
                "bottom": {
                    "x": 357,
                    "y": 52
                }
            }
        },
        ...
    ],
    "breadcrumbs": [
        ...
        {
            "name": "LN51L-KRA",
            "url": "LN51L-KRA/sysopt/001"
        },
        {
            "name": "STANDARD TOOL"
        }
    ],
    "subgroup": {
        "country_short_name": "US",
        "catalog_code": "671440",
        "category": "ENGINE",
        "complectation_code": "001",
        "illustration_short_name": "MT0887F",
        "short_name": "0901",
        "name": "STANDARD TOOL",
        "image": "https://acat.online/api/catalogs/CARS_FOREIGN/TOYOTA/US/671440/LN51L-KRA/sysopt/001/0901/MT0887F/image",
    }
}
```

### Значения numbers

| Имя | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| type | string | Да | Тип машины (в данном каталоге только CARS_FOREIGN - легковые иномарки)  |
| mark_short_name | string | Да | Краткое название марки (TOYOTA или LEXUS) |
| country_short_name | string | Да | Сокращение страны (например: US / JP ) |
| catalog_code | string | Да | Код каталога |
| model_code | string | Да | Код модели |
| sysopt | string | Да | Sysopt |
| complectation_code | string | Да | Код комплектации |
| disk | string | Да | Передается get параметром |
| group | string | Да | Код группы |
| illustration_short_name | string | Да | Код подгруппы |
| related_group | string | Да | Код связанной группы |
| related_illustration_short_name | string | Да | Код связанной подгруппы |
| number | string | Да | Номер детали |
| number_type | Integer | - | Тип детали |
| description | string | - | Описание |
| coordinate | Object | - | Координата |
| coordinate.top | Object | - | Верхняя координата |
| coordinate.top.x | Integer | - | Верхняя координата Х |
| coordinate.top.y | Integer | - | Верхняя координата Y |
| coordinate.bottom | Object | - | Нижняя координата |
| coordinate.bottom.x | Integer | - | Нижняя координата Х |
| coordinate.bottom.y | Integer | - | Нижняя координата Y |

### Значения subgroup

| Имя | Тип | Описание |
| :---- | :------: | :--------------- |
| country_short_name | string | Краткое название марки (TOYOTA или LEXUS) |
| catalog_code | string | Код каталога |
| category | string | Код категории |
| complectation_code | string | Код комплектации |
| short_name | string | Код группы |
| illustration_short_name | string | Код подгруппы |
| name | string | Название подгруппы |
| image | string | Путь до иллюстрации |


### Значения breadcrumbs

| Имя | Тип | Описание |
| :---- | :------: | :--------------- |
| name | string | Имя хлебной крошки |
| url | string | адрес текущей хлебной крошки |

## `GET /:type/:mark_short_name/:country_short_name/:model_code/:sysopt/:complectation_code/:group/:illustration/:number`

Для перехода к расширенной информации о детали выберите номер детали(number) в GET параметры
