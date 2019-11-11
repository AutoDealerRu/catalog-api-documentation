# Модели (models)

## `GET /:type/:mark`

Возвращает объект с двумя массивами models и breadcrumbs

| Конечная точка | Описание |
| :---- | :--------------- |
| GET /CARS_FOREIGN/mitsubishi | Модели марки Mitsubishi |
| GET /CARS_FOREIGN/ford | Модели марки Ford |

### Пример запроса

```bash
curl -H 'Authorization: <token>' -X GET https://acat.online/api/catalogs/CARS_FOREIGN/mitsubishi
```

### Пример ответа

```json
{
    "models": [
        {
            "id": "d044189982d7063dee143c0a7264f1ee",
            "name": "3000GT",
            "img": "//img.parts-catalogs.com/models/mitsubishi/3000GT.jpg"
        },
        ...
    ],
    "breadcrumbs": [
        ...,
        {
            "name": "Mitsubishi",
            "url": "mitsubishi"
        }
    ]
}
```

### Значения models

| Имя точка | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| id | string | Да | Идентификатор модели |
| name | string | - | Имя модели |
| img | string | - | Ссылка на изображение |

### Значения breadcrumbs

| Имя точка | Тип | Описание |
| :---- | :------: | :--------------- |
| name | string | Имя хлебной крошки |
| url | string | адрес текущей хлебной крошки |


## `GET https://acat.online/api/breadcrumbs[0].url/breadcrumbs[1].url/breadcrumbs[2].url/:model`