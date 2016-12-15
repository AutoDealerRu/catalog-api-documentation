# Группы (groups)

## `GET /:mark/:country_short_name/:directory/:modification`

Возвращает объект с image (изображение), groups и breadcrumbs (массивы)

### Примеры

| Конечная точка | Описание |
| :---- | :--------------- |
| [GET /NISSAN/EL/298/1] | Группы Nissan Европа (лев) ALMERA JPN MAKE N16 Модификации 1 |
| [GET /INFINITI/ER/019/1] | Группы Infiniti Европа (прав) G37 SEDAN V36 Модификации 1 |

### Пример запроса

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/CARS_FOREIGN/NISSAN/EL/298/1
```

### Пример ответа

```json
{
    "image": "/NISSAN/019/GENIMG/000000.gif",
    "groups": [
        {
           "mark": "INFINITI",
           "country_short_name": "ER",
           "directory": "019",
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
| mark | string | - | Название марки (NISSAN или INFINITI) |
| country_short_name | string | - | Сокращение страны (например: AR / GL ) |
| directory | string | - | Техсимвольное число содержашее в себе текущую модель+серию |
| group_short | string | Да | Сокращенное имя группы |
| group_name | string | - | Имя группы |
| coordinate | object | - | Координаты |
|   bottom | object | - | Нижние точки |
|       x | integer | - | Нижний Х |
|       y | integer | - | Нижний У |
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