# Комплектации (complectations)

## `GET /:type/:mark/:country_short_name/:catalog_code`

Возвращает объект с массивами complectations, breadcrumbs, abbreviations

### Примеры

| Конечная точка | Описание |
| :---- | :--------------- |
| GET /CARS_FOREIGN/TOYOTA/US/672450 | Комплектации Toyota 4-RUNNER TRUCK (США)|

### Пример запроса

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/CARS_FOREIGN/TOYOTA/US/672450
```

### Пример ответа

```json
{
    "complectations": [
        {
           "type": "CARS_FOREIGN",
           "country_short_name": "US",
           "catalog_code": "672450",
           "model_code": "RN120L-GKPSEA",
           "prod_start": "1989-04-01T00:00:00.000Z",
           "prod_end": "1991-08-01T00:00:00.000Z",
           "frame": "RN120",
           "complectation_code": "001",
           "sysopt": "sysopt",
           "mark_short_name": "TOYOTA",
           "model_name": "4-RUNNER TRUCK",
           "modifications": "RN8#,90,12#,VZN85,9#,VZN120",
           "engine_name": "22RE 2400CC EFI",
           "body_name": "",
           "grade_name": "SR-5 TYPE",
           "kpp_name": "AUTOMATIC TRANSMISSION,  4-SPEED FLOOR SHIFT",
           "other_name": "WAGON(4-RUNNER)",
           "engine_short_name": "22RE",
           "body_short_name": "",
           "grade_short_name": "SR5",
           "kpp_short_name": "ATM 4FC",
           "other_short_name": "WG EFI  USA  CBU  4D   JPP"
        },
        ...
    ],
    "breadcrumbs": [
        ...
        ,{
            "name": "4-RUNNER TRUCK",
            "url": "672450"
        },
    ],
    "abbreviations": [
        {
            "type_name": "Двигатель",
            "items": [
                {
                    "country_short_name": "US",
                    "catalog_code": "672450",
                    "sign": "22R",
                    "type": 1,
                    "type_name": "Двигатель",
                    "description": "2400CC",
                    "description_type": "ENGINE 1"
                },
                ...
            ]
        },
        ...
    ],
    "country": "США",
    "mark": "TOYOTA",
    "model": "4-RUNNER TRUCK"
}
```

### Значения complectations

| Имя | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| type | string | - | Тип машины (в данном каталоге только CARS_FOREIGN - легковые иномарки) |
| mark_short_name | string | Да | Краткое название марки (TOYOTA или LEXUS) |
| country_short_name | string | Да | Сокращение страны (например: US / JP ) |
| catalog_code | string | Да | Код каталога |
| model_code | string | Да | Код модели |
| sysopt | string | Да |  |
| complectation_code | string | Да | Код комплектации  |
| prod_start | Date | - | Дата производства "от" |
| prod_end | null/Date | - | Дата производства "до" |
| model_name | string | - | Наименование модели |
| modifications | string | - | Модификации |
| engine_short_name | string | - | Краткое наименование двигателя |
| engine_name | string | - | Двигатель |
| body_short_name | string | - | Краткое наименование кузова |
| body_name | string | - | Кузов |
| grade_short_name | string | - | Краткое наименование класса |
| grade_name | string | - | Класс |
| kpp_short_name | string | - | Краткое наименование КПП |
| kpp_name | string | - | КПП |
| other_short_name | string | - | Другая краткая информация |
| other_name | string | - | Другое |

### Значения breadcrumbs

| Имя | Тип | Описание |
| :---- | :------: | :--------------- |
| name | string | Имя хлебной крошки |
| url | string | адрес текущей хлебной крошки |

### Значения abbreviations (расшифровки)

| Имя | Тип | Описание |
| :---- | :------: | :--------------- |
| type_name | string |  Тип расшифровки |
| items[..].sign | array |  Аббревиатура |
| items[..].description | array |  Расшифровка |

### Другие данные

| Имя | Тип | Описание |
| :---- | :------: | :--------------- |
| country | string |  Страна |
| mark | string |  Марка |
| model | string |  Модель |


## `GET /:type/:mark_short_name/:country_short_name/:catalog_code/:model_code/:sysopt/:complectation_code`

Для перехода к списку групп нужно выбрать комплектацию и передать код модели (model_code), sysopt и код комлектации (complectation_code) в GET параметры
