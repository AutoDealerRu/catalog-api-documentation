# Номера (numbers)

## `GET /:mark/:country_short_name/:directory/:modification/:group`

### Возвращает объект содержащий:
1. image - путь до иллюстрации
2. images (картинками / закладками) - сразу все возможные; 
3. numbers (номера) - только для текущего изображения; 
4. breadcrumbs (хлебные крошки) - массив из имен и путей.

### Пример запроса (с демонстрацией различных типов номеров)

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/CARS_FOREIGN/INFINITI/CA/001/1/A/110/110C/003
```

### Пример ответа (частичный)

```json
{
  "previousGroup": {
      "type": "CARS_FOREIGN",
      "mark": "MERCEDES_BENZ",
      "country": "EU",
      "aggregation": "FG",
      "model": "201023",
      "catalog": "15C",
      "group": "68",
      "subgroup": "001",
      "sa": "56583",
      "stroke": "01",
      "name": "Обшивка - TRAY AT RIGHT BOTTOM OF HOUSING"
  },
  "nextGroup": {
      "type": "CARS_FOREIGN",
      "mark": "MERCEDES_BENZ",
      "country": "EU",
      "aggregation": "FG",
      "model": "201023",
      "catalog": "15C",
      "group": "29",
      "subgroup": "015",
      "name": "ПЕДАЛЬНЫЙ УЗЕЛ - PEDAL ASSEMBLY WITH BEARING"
  },
  "group": {
    "name": "ПЕДАЛЬНЫЙ УЗЕЛ"
  },
  "subgroup": {
    "name": "PEDAL ASSEMBLY HYDRAULICS"
  },
  "image": "https://212709.selcdn.ru/autocatalog-online/mercedes/BM_IMAGES_ARC_IMAGE_V/B29030000007.920416.png",
  "images": [
    ...,
    {
        "current": true,
        "type": "CARS_FOREIGN",
        "mark": "MERCEDES_BENZ",
        "country": "EU",
        "aggregation": "FG",
        "model": "201023",
        "catalog": "15C",
        "group": "29",
        "subgroup": "030",
        "position": 2,
        "image": "https://212709.selcdn.ru/autocatalog-online/mercedes/BM_IMAGES_ARC_IMAGE_V/B29030000007.920416.png",
        "points": [
          ...,    
          {
            "label": "11",
            "description": "РЕМКОМПЛЕКТ ГЛАВНЫЙ ЦИЛИНДР",
            "coordinate": {
                "bottom": {
                    "x": 884,
                    "y": 504
                },
                "top": {
                    "x": 854,
                    "y": 479
                }
            }
          },
          ...
        ]
    },
    ...
  ],
  "numbers": [
    ...,
	{
        "index": 0,
        "label": "5",
        "number": "A0012956806",
        "name": "ГЛАВНЫЙ ЦИЛИНДР",
        "footnotes": [],
        "note_number": [],
        "replaced_on": [
          "A2022900112"
        ],
        "same_numbers": []
    },
    ...
  ],
  "breadcrumbs": [
	...,
	{
        "name": "ПЕДАЛЬНЫЙ УЗЕЛ - PEDAL ASSEMBLY HYDRAULICS",
        "url": "29/030/2"
    }
  ]
}
```

### Значения previousGroup & nextGroup

| Имя точка | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| type | string | Да | Тип машины |
| mark | string | ДА | Название марки |
| country | string | ДА | Сокращение страны (например: EU ) |
| aggregation | string | ДА | Относительно какой части авто (агрегата) строить модельный ряд |
| model | string | ДА | Сокращение модели |
| catalog | string | ДА | Идентификатор каталога |
| group | string | ДА | Идентификатор группы |
| subgroup | string | ДА | Идентификатор подгруппы |
| sa | not exist/string | ДА | Идентификатор SA |
| stroke | not exist/string | ДА | Идентификатор stroke |
| name | string | - | Название (путь до) предыдущей или следующей группы изображений номеров |

### Значения image & images

| Имя точка | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| image | string | - | URL адрес текущего изображения |
| images[...].type | string | Да | Тип машины |
| images[...].mark | string | ДА | Название марки |
| images[...].country | string | ДА | Сокращение страны (например: EU ) |
| images[...].aggregation | string | ДА | Относительно какой части авто (агрегата) строить модельный ряд |
| images[...].model | string | ДА | Сокращение модели |
| images[...].catalog | string | ДА | Идентификатор каталога |
| images[...].group | string | ДА | Идентификатор группы |
| images[...].subgroup | string | ДА | Идентификатор подгруппы |
| images[...].sa | not exist/string | ДА | Идентификатор SA |
| images[...].stroke | not exist/string | ДА | Идентификатор stroke |
| images[...].position | integer | ДА | Порядковый номер изображения (может начинатся со значения больше 1) |
| images[...].current | not exist/boolean(true) | - | Текущее изображение |
| images[...].image | string | - | URL адрес текущего изображения |
| images[...].points | array | - | Координаты |
| images[...].points[...].label | object | - | Название точки на изображении (номер от 1 до ~500) |
| images[...].points[...].description | object | - | Описание точки (название детали) |
| images[...].points[...].coordinate.bottom | object | - | Нижние точки |
| images[...].points[...].coordinate.bottom.x | integer | - | Нижний Х |
| images[...].points[...].coordinate.bottom.y | integer | - | Нижний У |
| images[...].points[...].coordinate.top | object | - | Верхние точки |
| images[...].points[...].coordinate.top.x | integer | - | Верхний Х |
| images[...].points[...].coordinate.top.y | integer | - | Верхний У |

#### Пример построения ссылки для закладки (изображения)
#### `/:type/:mark/:country/:aggregation/:model/:catalog/:group/:subgroup(/:sa/:stroke)/:position`
#### ВАЖНО!!! Без параметра position изображение и номера будут, НО это всегда будет первая картанка из всей группы изображений
#### ВАЖНО!!! sa & stroke дописывать после subgroup если они есть (всегда парой идут)

### Значения numbers

| Имя точка | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| index | integer | - | Порядковый номен номера в списке (часто совпадает с label) |
| label | string | - | Обозначение на изображении (номер от 1 до ~500) |
| number | string | - | Номер детали |
| name | string | - | Название детали |
| replaced_on | array of string | - | Заменен на (один из номеров в этом спике) |
| same_numbers | array of string | - | Аналогичные детали |
| note_number | array of string | - | Точно не известно что это за номера (они были **отмечены красным**), возможно **не подходят / не совместимы** |
| footnotes | array of string | - | Примечания (сноски) |

### Значения breadcrumbs

| Имя точка | Тип | Описание |
| :---- | :------: | :--------------- |
| name | string | Имя хлебной крошки |
| url | string | адрес текущей хлебной крошки |