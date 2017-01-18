# Подномера деталей (subnumbers)

## `GET /:type/:mark/:country_short_name/:model_code/:sysopt/:complectation_code/:group/:illustration/:number`

Возвращает объект с массивом subnumbers

### Примеры

| Конечная точка | Описание |
| :---- | :--------------- |
| GET /CARS_FOREIGN/TOYOTA/US/671440/LN51L-KRA/sysopt/001/0901/MT0887F/09113 | Список подномеров детали № 09113 (US 4-RUNNER TRUCK комплектация LN51L-KRA группа STANDARD TOOL (Двигатель, топливная система и инструменты)) |

### Пример запроса

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/CARS_FOREIGN/TOYOTA/US/671440/LN51L-KRA/sysopt/001/0901/MT0887F/09113
```

### Пример ответа

```json
{
    "subnumbers": [
        {
            "country_short_name": "US",
            "catalog_code": 671440,
            "number": "09113",
            "amount": "1",
            "subnumber": "911335070",
            "date_start": "Mon Aug 01 1983 00:00:00 GMT+0600 (SVEST)",
            "date_end": "Thu Aug 01 1985 00:00:00 GMT+0600 (SVEST)",
            "analogs": [
                "09113-35071"
            ]
        },
        ...
    ]
}
```

### Значения subnumbers

| Имя | Тип | Описание |
| :---- | :------: | :--------------- |
| country_short_name | string | Краткое название марки (TOYOTA или LEXUS) |
| catalog_code | integer | Код каталога |
| number | string | Основной номер |
| amount | string | Количество |
| subnumber | string | Номер |
| date_start | string | Дата производства "от" |
| date_end | string | Дата производства "до" |
| analogs[] | array | Список номеров деталей аналогов |

