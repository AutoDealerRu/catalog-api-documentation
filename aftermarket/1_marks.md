# Марки (marks)

## `GET /:type/:mark`

Возвращает объект с двумя массивами marks и breadcrumbs

| Конечная точка | Описание |
| :---- | :--------------- |
| GET /CARS_FOREIGN/AFTERMARKET | Легковые марки машин |
| GET /TRUCKS_FOREIGN/AFTERMARKET | Грузовые марки машин |

### Пример запроса

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/CARS_FOREIGN/AFTERMARKET
```

### Пример ответа

```json
{
    "marks": [
        {
            "type": "CARS_FOREIGN",
            "mark": "AFTERMARKET",
            "mark_name": "AC",
            "image": "AFTERMARKET/marks/png/ac.png",
            "mark_short_name": "AC"
        },
        {
            "type": "CARS_FOREIGN",
            "mark": "AFTERMARKET",
            "mark_name": "ACURA",
            "image": "AFTERMARKET/marks/png/acura.png",
            "mark_short_name": "ACURA"
        },
        ...
    ],
    "breadcrumbs": [
        ...
        ,{
            "name": "Aftermarket",
            "url": "AFTERMARKET"
        }
    ]
}
```

### Значения marks

| Имя точка | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| type | string | - | Тип кузова |
| mark | string | - | Название каталога (всегда будет AFTERMARKET) |
| mark_name | string | - | Название марки (ACURA, HYUNDAI и т.д.) |
| image | string | - | Путь до изображения |
| mark_short_name | string | Да | Сокращенное название марки |

### Значения breadcrumbs

| Имя точка | Тип | Описание |
| :---- | :------: | :--------------- |
| name | string | Имя хлебной крошки |
| url | string | Адрес текущей хлебной крошки |


## `GET /:type/:mark/:mark_short_name`

Для перехода к списку моделей нужно выбрать марк и передать ее сокращение (mark_short_name) в GET параметры