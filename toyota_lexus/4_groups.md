# Группы (groups)

## `GET /:type/:mark_short_name/:country_short_name/:model_code/:sysopt/:compl_code`

Возвращает объект с массивами groups, breadcrumbs и объектом complectation

### Примеры

| Конечная точка | Описание |
| :---- | :--------------- |
| GET /CARS_FOREIGN/TOYOTA/US/671440/LN51L-KRA/sysopt/001 | Список групп US 4-RUNNER TRUCK комплектация LN51L-KRA |

### Пример запроса

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/CARS_FOREIGN/TOYOTA/US/671440/LN51L-KRA/sysopt/001
```

### Пример ответа

```json
{
    "breadcrumbs": [
        ...,
        {
            "name": "4-RUNNER TRUCK",
            "url": "671440"
        },
        {
            "name": "LN51L-KRA"
        }
    ],
    "complectation": {
        "country_short_name": "US",
        "catalog_code": "671440",
        "model_code": "LN51L-KRA",
        "prod_start": "1984-08-01T00:00:00.000Z",
        "prod_end": "1985-08-01T00:00:00.000Z",
        "complectation_code": "001",
        "sysopt": "sysopt",
        "mark_short_name": "TOYOTA",
        "model_name": "4-RUNNER TRUCK",
        "modifications": "RN5#,6#,7#,VZN6#,LN5#,6#",
        "engine_name": "2L 2400CC DIESEL",
        "body_name": "LOW DECK,PICKUP(STANDARD DECK 1-SIDE OPEN)",
        "grade_name": "STANDARD TYPE",
        "kpp_name": "MANUAL TRANSMISSION,  4-SPEED FLOOR SHIFT",
        "other_name": "REGULAR CAB G TYPE 0.5TONS ST TYPE:SINGLE TIRE",
        "engine_short_name": "2L",
        "body_short_name": "T1",
        "grade_short_name": "STD",
        "kpp_short_name": "MTM 4F",
        "other_short_name": "RCB G HLF ST USA  DSL  CBU"
    },
    "groups": [
        {
            "name": "Двигатель, топливная система и инструменты",
            "category": "ENGINE",
            "subgroups": [
                {
                    "country_short_name": "US",
                    "catalog_code": "671440",
                    "category": "ENGINE",
                    "complectation_code": "001",
                    "illustration_short_name": "MT0887F",
                    "short_name": "0901",
                    "name": "STANDARD TOOL",
                    "image": "http://auto2d.com/img/toyota/ImgIllIndex/US/671440/MT0887F.png"
                },
                ...
            ]
        },
        ...
    ]
}
```

### Значения groups

| Имя | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| name | string | - | Наименование  |
| category | string | - | Алиас группы |
| subgroups[] | array | - | Подгруппы |
| subgroups[].country_short_name | string | Да | Краткое название страны |
| subgroups[].catalog_code | string | Да | Код каталога |
| subgroups[].complectation_code | string | Да | Код комплектации |
| subgroups[].short_name | string | Да | Код группы |
| subgroups[].illustration_short_name | string | Да | Код подгруппы |
| subgroups[].name | string | - | Название подгруппы |
| subgroups[].image | string | - | Путь до картинки подгруппы |
| subgroups[].category | string | - | Родительская категория |

### Значения объекта complectation

| Имя | Тип | Описание |
| :---- | :------: | :--------------- |
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

## `GET /:type/:mark_short_name/:country_short_name/:model_code/:sysopt/:complectation_code/:group/:illustration`

Для перехода к списку деталей нужно выбрать подгруппу и передать код группы (group) и код подгруппы (illustration) в GET параметры


