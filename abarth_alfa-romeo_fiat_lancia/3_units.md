# Основные узлы

## `GET /:mark/:model_short_name/:modification_short_name`

Возвращает объект с двумя массивами units и breadcrumbs

| Конечная точка | Описание |
| :---- | :--------------- |
| GET /CARS_FOREIGN/ABARTH | Серии марки Abarth Легковых иномарок |
| GET /CARS_FOREIGN/ALFA-ROMEO | Серии марки Alfa-Romeo Легковых иномарок |
| GET /CARS_FOREIGN/FIAT | Серии марки Fiat Легковых иномарок |
| GET /CARS_FOREIGN/LANCIA | Серии марки Lancia Легковых иномарок |

### Пример запроса

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/CARS_FOREIGN/FIAT/CIN/3P
```

### Пример ответа

```json
{
    "units": [
        {
            "short_name": 101,
            "full_name": "БЛОК И ГОЛОВКА ЦИЛИНДРОВ",
            "filename": "24/2415A72DC753B8251C229790FA44F804.png",
            "modification_short_name": "3P"
        }
        ...
    ],
    "breadcrumbs": [
        ...
        {
            "name": "NUOVA 500 (2007-2012)",
            "url": "3P"
        }
    ]
}
```

### Значения units

| Имя | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| short_name | integer | Да | Идентификатор |
| full_name | string | - | Наименование |
| filename | string | - | URL до изображения |
| modification_short_name | string | - | Идентификатор модификации |

### Значения breadcrumbs

| Имя | Тип | Описание |
| :---- | :------: | :--------------- |
| name | string | Имя хлебной крошки |
| url | string | адрес текущей хлебной крошки |


## `GET /:mark/:model_short_name/:modification_short_name/:short_name`

Для перехода к подгруппам нужно выбрать основную группу и передать ее сокращение (short_name) в GET параметры