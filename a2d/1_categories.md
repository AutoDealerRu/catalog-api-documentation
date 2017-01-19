# Категории

## `GET /:mark`

Возвращает объект с двумя массивами categories и breadcrumbs

### Пример запроса

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/CARS_NATIVE/VAZ
```

### Пример ответа

```json
{
    "categories": [
        {
            "name": "Основной",
            "value": "GENERAL",
            "type": "CARS_NATIVE",
            "mark": "VAZ"
        },
        {
            "name": "Архивный",
            "value": "ARCHIVE",
            "type": "CARS_NATIVE",
            "mark": "VAZ"
        }
    ],
    "breadcrumbs": [
        ...
        {
            "name": "ВАЗ",
            "url": "VAZ"
        }
    ]
}
```

### Значения categories

| Имя | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| name | string | - | Название |
| value | string | Да | Идентификатор |
| type | string | - | Тип транспортного средства |
| mark | string | - | Идентификатор марки |

### Значения breadcrumbs

| Имя | Тип | Описание |
| :---- | :------: | :--------------- |
| name | string | Имя хлебной крошки |
| url | string | адрес текущей хлебной крошки |


## `GET /:mark/:value`

Для перехода к списку модификаций нужно выбрать категорию и передать ее идентификатор (value) в GET параметры