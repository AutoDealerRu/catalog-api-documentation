# Countries (страны)

## `GET /:mark/`

<table>
    <thead>
        <tr>
            <th>Конечная точка</th>
            <th>Описание</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>GET /:NISSAN</td>
            <td>Список доступный стран Nissan</td>
        </tr>
        <tr>
            <td>GET /:INFINITI</td>
            <td>Список доступный стран Infiniti</td>
        </tr>
    </tbody>
</table>

[users]: /v3_resources/users.md
[channels]: /v3_resources/channels.md

## `GET /:mark/`

Возвращает объект с двумя массивами countries и breadcrumbs

### Пример запроса

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/CARS_FOREIGN/NISSAN
```

### Пример ответа

```json
{
    "countries": [
        {
        "type": "CARS_FOREIGN",
        "mark": "NISSAN",
        "country_short_name": "AR",
        "full_name": "Австралия"
        },
        ...
    ],
    "breadcrumbs": [
        {
        "name": "Каталог",
        "url": "/catalogs"
        },
        ...
    ]
}
```

### Значения countries

| Имя точка | Тип | Описание |
| ---- | --------------- | --------------- |
| type | string | Тип машины (в данном каталоге только CARS_FOREIGN - легковые иномарки) |
| mark | string | Название марки (NISSAN или INFINITI) |
| country_short_name | string | Сокращение страны (например: AR / GL ) |
| full_name | string | Полное название страны |

### Значения breadcrumbs

| Имя точка | Тип | Описание |
| ---- | --------------- | --------------- |
| name | string | Имя хлебной крошки |
| url | string | адрес текущей хлебной крошки |