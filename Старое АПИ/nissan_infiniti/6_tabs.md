# Изображения / Закладки (tabs)

## `GET /:mark/:country_short_name/:directory/:modification/:group/:subgroup`

### Примеры

| Конечная точка | Описание |
| :---- | :--------------- |
| GET /NISSAN/EL/298/1/A/101 | Изображения Nissan ALMERA JPN MAKE N16 |

### Пример запроса

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/CARS_FOREIGN/NISSAN/EL/298/1/A/101
```

## Пример ответа, если изображение есть - [Пример](/Старое%20АПИ/nissan_infinitissan_infiniti/7_numbers.md#Пример-ответа-частичный)
## Пример ответа, если изображение нет - [ниже](/Старое%20АПИ/nissan_infinitissan_infiniti/6_tabs.md#Пример-ответа)

### ВАЖНО! Может придти ответ `tab: NULL` - изображения нет, следовательно номеров нет
### Пример запроса

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/CARS_FOREIGN/NISSAN/GL/008/7/C/208
```

### Пример ответа

```json
{
    "tab": null,
    "breadcrumbs": [
        ...,
        {
            "name": "CATALYST CONVERTER,EXHAUST FUEL & URE IN",
            "url": "208"
        }
    ]
}
```