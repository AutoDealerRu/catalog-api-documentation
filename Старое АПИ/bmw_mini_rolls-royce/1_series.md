# Серии

## `GET /:mark`

Возвращает объект с двумя массивами series и breadcrumbs

| Конечная точка | Описание |
| :---- | :--------------- |
| GET /CARS_FOREIGN/BMW | Серии марки BMW Легковых иномарок |
| GET /CARS_FOREIGN/ROLLS-ROYCE | Серии марки Rolls-Royce Легковых иномарок |
| GET /CARS_FOREIGN/MINI | Серии марки Mini Легковых иномарок |
| GET /MOTORCYCLE/BMW | Серии марки BMW Мотоциклов |

### Пример запроса

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/CARS_FOREIGN/BMW
```

### Пример ответа

```json
{
    "series": [
        {
            "type": "CARS_FOREIGN",
            "short_name": "E81",
            "name": "1' E81",
            "index": 3,
            "mark_short_name": "BMW",
            "catalog_type": "VT",
            "image": "https://212709.selcdn.ru/autocatalog-online/BMW/w_grafik/163627_t.jpg"
        },
        ...
    ],
    "breadcrumbs": [
        ...
        {
            "name": "BMW",
            "url": "BMW"
        }
    ]
}
```

### Значения series

| Имя | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| type | string | - | Тип кузова |
| short_name | string | Да | Идентификатор серии |
| name | string | - | Полное наименование серии |
| index | integer | - | Порядковый номер |
| mark_short_name | string | - | Стандартизированное название марки |
| catalog_type | string | - | Тип каталога (enum, VT - современный каталог, ST - живая традиция) |
| image | string | - | URL до изображения |

### Значения breadcrumbs

| Имя | Тип | Описание |
| :---- | :------: | :--------------- |
| name | string | Имя хлебной крошки |
| url | string | адрес текущей хлебной крошки |


## `GET /:mark/:short_name`

Для перехода к списку моделей нужно выбрать серию и передать ее сокращение (short_name) в GET параметры