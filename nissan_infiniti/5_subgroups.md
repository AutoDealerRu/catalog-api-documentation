# Подгруппы (subgroups)

## `GET /:mark/:country_short_name/:directory/:modification/:group`

### Возвращает объект содержащий:
1. images - все возможные изображения (закладки); 
2. subgroups - подгруппы для всех картинок; 
3. breadcrumbs (хлебные крошки) - массив из имен и путей.

Возвращает объект с images, subgroups и breadcrumbs (мыссивы)

### Примеры

| Конечная точка | Описание |
| :---- | :--------------- |
| GET /NISSAN/EL/298/1/A | Подгруппы Nissan ALMERA JPN MAKE N16 |
| GET /INFINITI/ER/019/1/A | Подгруппы Infiniti G37 SEDAN V36 |

### Пример запроса

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/CARS_FOREIGN/NISSAN/EL/298/1/A
```

### Пример ответа

```json
{
    "images": [
        "NISSAN/EL/298/GRPIMG/000000.gif",
        ...
    ],
    "subgroups": [
        [
            {
                "mark": "NISSAN",
                "country_short_name": "EL",
                "directory": "298",
                "group_short": "A",
                "image_group": 1,
                "figure": "101",
                "group_name": "BARE & SHORT ENGINE",
                "coordinate": {
                    "bottom": {
                        "x": 775,
                        "y": 72
                    },
                    "top": {
                        "x": 739,
                        "y": 56
                    }
                }
            },
            ...
        ],
        ...
    ],
    "breadcrumbs": [
        ...
        ,{
            "name": "ENGINE MECHANICAL",
            "url": "A"
        }
    ]
}
```

### Значения images

| Имя точка | Тип | Описание |
| :---- | :------: | :--------------- |
| images | Array | Пути до изображений |
| images[0] | string | Путь до картинки |

### Значения subgroups

| Имя точка | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| mark | string | - | Название марки (NISSAN или INFINITI) |
| country_short_name | string | - | Сокращение страны (например: AR / GL ) |
| directory | string | - | Техсимвольное число содержашее в себе текущую модель+серию |
| group_short | string | - | Сокращенное имя группы |
| image_group | number | - | номер ключа в массиве images |
| figure | string | Да | Номер подгруппы |
| group_name | string | - | Сокращенное имя подгруппы |
| coordinate | object | - | Координаты |
| coordinate.bottom | object | - | Нижние точки |
| coordinate.bottom.x | integer | - | Нижний Х |
| coordinate.bottom.y | integer | - | Нижний У |
| coordinate.top | object | - | Верхние точки |
| coordinate.top.x | integer | - | Верхний Х |
| coordinate.top.y | integer | - | Верхний У |

#### ВАЖНО! В массиве subgroups количество подмассивов равно количеству изображений.
#### Все подгрупы в массиве subgroups[0] относятся к изображению images[0] и т.д.

### Значения breadcrumbs

| Имя точка | Тип | Описание |
| :---- | :------: | :--------------- |
| name | string | Имя хлебной крошки |
| url | string | адрес текущей хлебной крошки |


## `GET /:mark/:country_short_name/:directory/:modification/:group_short/:figure`

Для перехода к списку номеров нужно выбрать подгруппу и передать ее сокращение (figure) в GET параметры