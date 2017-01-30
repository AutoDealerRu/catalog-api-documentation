# Модели

## `GET /:mark`

Возвращает объект с двумя массивами models и breadcrumbs

| Конечная точка | Описание |
| :---- | :--------------- |
| GET /CARS_FOREIGN/ABARTH | Серии марки Abarth Легковых иномарок |
| GET /CARS_FOREIGN/ALFA-ROMEO | Серии марки Alfa-Romeo Легковых иномарок |
| GET /CARS_FOREIGN/FIAT | Серии марки Fiat Легковых иномарок |
| GET /CARS_FOREIGN/LANCIA | Серии марки Lancia Легковых иномарок |

### Пример запроса

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/CARS_FOREIGN/FIAT
```

### Пример ответа

```json
{
    "models": [
        {
            "short_name": "FRM",
            "full_name": "FREEMONT",
            "brand_short_name": "FIAT",
            "type": "CARS_FOREIGN",
            "image": "https://212709.selcdn.ru/autocatalog-online/Fiat/appsrv_img/F/model_imgs/small/FRM"
        },
        ...
    ],
    "breadcrumbs": [
        ...
        {
            "name": "FIAT",
            "url": "FIAT"
        }
    ]
}
```

### Значения models

| Имя | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| short_name | string | Да | Идентификатор |
| full_name | string | - | Наименование |
| brand_short_name | string | - | Идентификатор бренда |
| type | string | - | Тип кузова |
| image | string | - | URL до изображения |

### Значения breadcrumbs

| Имя | Тип | Описание |
| :---- | :------: | :--------------- |
| name | string | Имя хлебной крошки |
| url | string | адрес текущей хлебной крошки |


## `GET /:mark/:short_name`

Для перехода к списку модификаций нужно выбрать модель и передать ее сокращение (short_name) в GET параметры