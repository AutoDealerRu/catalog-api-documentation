# Модели (models)

## `GET /:type/:mark/:model`

Возвращает объект содержащий filters, modifications, breadcrumbs, pages, page, itemsCount

| Конечная точка | Описание |
| :---- | :--------------- |
| GET /CARS_FOREIGN/mitsubishi/d044189982d7063dee143c0a7264f1ee | Фильтры и модификации Mitsubishi 3000GT |

### Пример запроса

```bash
curl -H 'Authorization: <token>' -X GET https://acat.online/api/catalogs/CARS_FOREIGN/mitsubishi/d044189982d7063dee143c0a7264f1ee
```

### Пример ответа

```json
{
    "modifications": [
        {
            "model": {
                "name": "3000GT",
                "id": "d044189982d7063dee143c0a7264f1ee"
            },
            "id": "817904ab9b87057e1baa7033cdf94530",
            "name": "3000GT(EUR)",
            "params": [],
            "filters": null,
            "transmission": {
                "type": null,
                "name": null
            },
            "engine": null,
            "bodyType": null,
            "steeringId": null,
            "steering": null,
            "year": "1990",
            "region": "Европа",
            "description": "PREMIUM LINE(DOHC),5FM/T             CAL\r\n3000/2WD\r\nModification: Z11A\r\nClassification: MNPML7M\r\nProduction: 01.04.1990 - 03.06.2000",
            "catalogId": "mitsubishi"
        },
        ...
    ],
    "filters": [
      {
          "sortOrder": 1,
          "values": [
              {
                  "text": "2000",
                  "id": "6448e17c83f950cb8eeef93fa5caa63a"
              },
              ...
          ],
          "name": {
              "text": "Год",
              "key": "year",
              "id": "year"
          }
      },
    ],
    "breadcrumbs": [
        ...,
        {
            "name": "3000GT",
            "url": "d044189982d7063dee143c0a7264f1ee"
        }
    ],
    "pages": [1, 2, 3, ...],
    "page": 1,
    "itemsCount": 372,
    "showEngine": false,
    "showTransmission": false
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