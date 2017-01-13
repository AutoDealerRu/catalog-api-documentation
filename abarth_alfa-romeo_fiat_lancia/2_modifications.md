# Модификации

## `GET /:mark/:model_short_name`

Возвращает объект с двумя массивами modifications и breadcrumbs

| Конечная точка | Описание |
| :---- | :--------------- |
| GET /CARS_FOREIGN/ABARTH | Серии марки Abarth Легковых иномарок |
| GET /CARS_FOREIGN/ALFA-ROMEO | Серии марки Alfa-Romeo Легковых иномарок |
| GET /CARS_FOREIGN/FIAT | Серии марки Fiat Легковых иномарок |
| GET /CARS_FOREIGN/LANCIA | Серии марки Lancia Легковых иномарок |

### Пример запроса

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/CARS_FOREIGN/FIAT/CIN
```

### Пример ответа

```json
{
    "modifications": [
        {
            "short_name": "3P",
            "full_name": "NUOVA 500 (2007-2012)",
            "model_short_name": "CIN"
        },
        ...
    ],
    "breadcrumbs": [
        ...
        {
            "name": "500",
            "url": "CIN"
        }
    ]
}
```

### Значения modifications

| Имя | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| short_name | string | Да | Идентификатор |
| full_name | string | - | Наименование |
| model_short_name | string | - | Идентификатор модели |

### Значения breadcrumbs

| Имя | Тип | Описание |
| :---- | :------: | :--------------- |
| name | string | Имя хлебной крошки |
| url | string | адрес текущей хлебной крошки |


## `GET /:mark/:model_short_name/:short_name`

Для перехода к списку основных узлов (units) нужно выбрать модификацию и передать ее сокращение (short_name) в GET параметры