# Группы (groups)

## `GET /:mark/:country_short_name/:directory/:modification`

Возвращает объект с image (изображение), groups и breadcrumbs (массивы)

### Примеры

| Конечная точка | Описание |
| :---- | :--------------- |
| GET /NISSAN/EL/298/1 | Группы Nissan Европа (лев) ALMERA JPN MAKE N16 Модификации 1 |
| GET /INFINITI/ER/019/1 | Группы Infiniti Европа (прав) G37 SEDAN V36 Модификации 1 |

### Пример запроса

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/CARS_FOREIGN/NISSAN/EL/298/1
```

### Пример ответа

```json
{
    "image": "https://212709.selcdn.ru/autocatalog-online/nissan/EL/298/GENIMG/000000.gif",
    "groups": [
        {
           "type": "CARS_FOREIGN",
           "mark": "INFINITI",
           "country_short_name": "ER",
           "directory": "019",
           "modification": 1,
           "group_short": "A",
           "group_name": "ENGINE MECHANICAL",
           "coordinate": {
               "bottom": {
                   "x": 336,
                   "y": 376
               },
               "top": {
                   "x": 308,
                   "y": 351
               }
           }
        },
        ...
    ],
    "breadcrumbs": [
        ...
        ,{
            "name": "QG18DE,S,AT",
            "url": "1"
        }
    ]
}
```

### Значения image & groups

| Имя точка | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| image | null/string | - | Путь до изображения |
| type | string | Да | Тип машины (всегда CARS_FOREIGN) |
| mark | string | Да | Название марки (NISSAN или INFINITI) |
| country_short_name | string | Да | Сокращение страны (например: AR / GL ) |
| directory | string | Да | Техсимвольное число содержашее в себе текущую модель+серию |
| modification | integer | Да | Номер модификации |
| group_short | string | Да | Сокращенное имя группы |
| group_name | string | - | Имя группы |
| coordinate | object | - | Координаты |
| coordinate.bottom | object | - | Нижние точки |
| coordinate.bottom.x | integer | - | Нижний Х |
| coordinate.bottom.y | integer | - | Нижний У |
| coordinate.top | object | - | Верхние точки |
| coordinate.top.x | integer | - | Верхний Х |
| coordinate.top.y | integer | - | Верхний У |

### Значения breadcrumbs

| Имя точка | Тип | Описание |
| :---- | :------: | :--------------- |
| name | string | Имя хлебной крошки |
| url | string | адрес текущей хлебной крошки |


## `GET /:mark/:country_short_name/:directory/:modification/:group_short`

Для перехода к списку подгрупп нужно выбрать группу и передать ее сокращение (group_short) в GET параметры