# Подгруппы (subgroups)

## `GET /:mark/:country_short_name/:directory/:modification/:group`

### Возвращает объект содержащий:
1. images (картинками / закладками) - сразу все возможные; 
2. numbers (номера) - только для текущего изображения; 
3. breadcrumbs (хлебные крошки) - массив из имен и путей.

### Пример запроса (с демонстрацией различных типов номеров)

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/CARS_FOREIGN/INFINITI/CA/001/1/A/110/110C/003
```

### Пример ответа (частичный)

```json
{
  "images": [
    ...,
    {
        "type": "CARS_FOREIGN",
        "mark": "INFINITI",
        "country_short_name": "CA",
        "directory": "001",
        "modification": 1,
        "group": "A",
        "subgroup": "110",
        "figure": "110C",
        "section": "003",
        "current": true
    },{
        "type": "CARS_FOREIGN",
        "mark": "INFINITI",
        "country_short_name": "CA",
        "directory": "001",
        "modification": 1,
        "group": "A",
        "subgroup": "110",
        "figure": "110C",
        "section": "004"
    }
  ],
  "numbers": [
	{
        "mark": "INFINITI",
        "country_short_name": "CA",
        "directory": "001",
        "number": "11121Z",
        "description": "GASKET-LIQUID",
        "number_type": "SUBNUMBERS",
        "items": [
            {
                "number_group": "11121Z",
                "from_date": "2001-01-01T00:00:00.000Z",
                "to_date": "2005-12-01T00:00:00.000Z",
                "number": "KP71000150",
                "applicability": "VK45DE"
            },
            {
                "number_group": "11121Z",
                "from_date": "2005-12-01T00:00:00.000Z",
                "to_date": null,
                "number": "KP71000150",
                "applicability": "VK45DE"
            }
        ],
        "coordinate": {
            "top": {
                "x": 353,
                "y": 485
            },
            "bottom": {
                "x": 420,
                "y": 501
            }
        },
    },
    ...,
    {
        "mark": "INFINITI",
        "country_short_name": "CA",
        "directory": "001",
        "figure": "110C",
        "section": "003",
        "number": "0836041225",
        "description": "SCREW-MACHINE",
        "coordinate": {
            "top": {
                "x": 400,
                "y": 253
            },
            "bottom": {
                "x": 511,
                "y": 269
            }
        },
        "number_type": "NUMBER"
     },
     ...,
     {
        "group": "A",
        "modification": 1,
        "type": "CARS_FOREIGN",
        "mark": "INFINITI",
        "country_short_name": "CA",
        "directory": "001",
        "figure": "110C",
        "section": "003",
        "number": "135",
        "description": "FRONT COVER,VACUUM PUMP & FITTING",
        "number_type": "SECTION",
        "items": [],
        "coordinate": {
            "top": {
                "x": 275,
                "y": 466
            },
            "bottom": {
                "x": 334,
                "y": 482
            }
        },
        "number_type": "SECTION"
     },
     ...
  ],
  "breadcrumbs": [
	...,
	{
	  "name": "CYLINDER BLOCK & OIL PAN",
      "url": "110"
	}
  ]
}
```

### Значения images

| Имя точка | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| type | string | Да | Тип машины (всегда CARS_FOREIGN) |
| mark | string | ДА | Название марки (NISSAN или INFINITI) |
| country_short_name | string | ДА | Сокращение страны (например: AR / GL ) |
| directory | string | ДА | Техсимвольное число содержашее в себе текущую модель+серию |
| modification | integer | ДА | Номер модификации |
| group | string | ДА | Сокращенное имя группы (group_short) |
| subgroup | string | ДА | Номер подгруппы |
| figure | string | ДА | Номер фигуры |
| section | string | ДА | Номер изображения (закладки / секции) |
| current | boolean | - | Текущее изображение (Да или не будет этой переменной) |

#### Пример построения ссылки для закладки (изображения)
#### `/:type/:mark/:country_short_name/:directory/:modification/:group/:subgroup/:figure/:section`

#### Пример запроса загрузки изображения
#### `GET /:mark/:country_short_name/:directory/:modification/:group/:subgroup/:figure/:section/image`
```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/CARS_FOREIGN/INFINITI/CA/001/1/A/110/110C/003/image
```
#### В ответ придет изображение, если статус 200 (схема) или 404 ("изображение не найдено", с изображением - заглушкой)

## Типы номеров:

'SUBNUMBERS' - содержит массив items содержащий в себе именно номера (может быть пустым)
'NUMBER' - это именно номер
'SECTION' - это ссылка на другую подгруппу
'UNKNOWN' - неизвестный тип (такой можно выводить как 'NUMBER', очень редко встречаются)

### Значения numbers где number_type = 'SUBNUMBERS'

| Имя точка | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| number | string | - | Обозначение на изображении |
| description | string | - | Описание / название |
| number_type | string | - | Тип номера |
| items | array | - | Номера |
| items.number_group | String | - | Обозначение на изображении |
| items.from_date | date | - | Дата начала производства |
| items.to_date | date | - | Дата окончания производства |
| items.number | string | - | Номер детали |
| items.applicability | string | - | Применяемость детали |
| coordinate | object | - | Координаты |
| coordinate.bottom | object | - | Нижние точки |
| coordinate.bottom.x | integer | - | Нижний Х |
| coordinate.bottom.y | integer | - | Нижний У |
| coordinate.top | object | - | Верхние точки |
| coordinate.top.x | integer | - | Верхний Х |
| coordinate.top.y | integer | - | Верхний У |

### Значения numbers где number_type = 'NUMBER' или 'UNKNOWN'

| Имя точка | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| number | string | - | Номер и обозначение на изображении |
| description | string | - | Описание / название |
| number_type | string | - | Тип номера |
| coordinate | object | - | Координаты |
| coordinate.bottom | object | - | Нижние точки |
| coordinate.bottom.x | integer | - | Нижний Х |
| coordinate.bottom.y | integer | - | Нижний У |
| coordinate.top | object | - | Верхние точки |
| coordinate.top.x | integer | - | Верхний Х |
| coordinate.top.y | integer | - | Верхний У |

### Значения numbers где number_type = 'SECTION'

| Имя точка | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| type | string | Да | Тип машины (всегда CARS_FOREIGN) |
| mark | string | Да | Название марки (NISSAN или INFINITI) |
| country_short_name | string | Да | Сокращение страны (например: AR / GL ) |
| directory | string | Да | Техсимвольное число содержашее в себе текущую модель+серию |
| modification | integer | Да | Номер модификации |
| group | string | Да | Номер модификации |
| number | string | Да | Номер и обозначение на изображении |
| description | string | - | Название группы |
| number_type | string | - | Тип номера |
| coordinate | object | - | Координаты |
| coordinate.bottom | object | - | Нижние точки |
| coordinate.bottom.x | integer | - | Нижний Х |
| coordinate.bottom.y | integer | - | Нижний У |
| coordinate.top | object | - | Верхние точки |
| coordinate.top.x | integer | - | Верхний Х |
| coordinate.top.y | integer | - | Верхний У |

#### Пример построения ссылки для number_type = 'SECTION'
#### `/:type/:mark/:country_short_name/:directory/:modification/:group/:number`

### Значения breadcrumbs

| Имя точка | Тип | Описание |
| :---- | :------: | :--------------- |
| name | string | Имя хлебной крошки |
| url | string | адрес текущей хлебной крошки |