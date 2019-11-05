# Группы & подгруппы (groups & subgroups)

## `GET /:type/:mark/:model/:modification[/:group][?criteria=]`

Возвращает объект содержащий model, modification, breadcrumbs, groups, criteria, group

| Конечная точка | Описание |
| :---- | :--------------- |
| GET /CARS_FOREIGN/mitsubishi/d044189982d7063dee143c0a7264f1ee/817904ab9b87057e1baa7033cdf94530 | Первый уровень групп |
| GET /CARS_FOREIGN/mitsubishi/d044189982d7063dee143c0a7264f1ee/817904ab9b87057e1baa7033cdf94530/MfCfmoAxMQ | Второй уровень групп |

### Пример запроса

```bash
curl -H 'Authorization: <token>' -X GET https://acat.online/api/catalogs/CARS_FOREIGN/mitsubishi/d044189982d7063dee143c0a7264f1ee/817904ab9b87057e1baa7033cdf94530
curl -H 'Authorization: <token>' -X GET https://acat.online/api/catalogs/CARS_FOREIGN/mitsubishi/d044189982d7063dee143c0a7264f1ee/817904ab9b87057e1baa7033cdf94530/MfCfmoAxMQ
```

### Пример ответа

```json
{
    "groups": [
      {
          "description": null,
          "img": null,
          "name": "Двери",
          "hasParts": false,
          "hasSubgroups": true,
          "parentId": "MA",
          "id": "MfCfmoA0Mw"
      },
      ...
    ],
    "model": {
        "img": "//img.parts-catalogs.com/models/mitsubishi/3000GT.jpg",
        "name": "3000GT",
        "id": "d044189982d7063dee143c0a7264f1ee"
    },
    "modification": {
        "model": {
            "name": "3000GT",
            "id": "d044189982d7063dee143c0a7264f1ee"
        },
        "id": "817904ab9b87057e1baa7033cdf94530",
        "name": "3000GT(EUR)",
        "transmission": {
            "type": null,
            "name": null
        },
        "engine": null,
        "bodyType": null,
        "steering": null,
        "year": "1990",
        "region": "Европа",
        "description": "PREMIUM LINE(DOHC),5FM/T             CAL\r\n3000/2WD\r\nModification: Z11A\r\nClassification: MNPML7M\r\nProduction: 01.04.1990 - 03.06.2000",
        "catalogId": "mitsubishi"
    },
    "breadcrumbs": [
        ...,
        {
            "name": "3000GT(EUR)",
            "url": "817904ab9b87057e1baa7033cdf94530"
        }
    ],
    "criteria": null,
    "group": null
}
```

### Значения groups

| Имя точка | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| id | string | Да | Идентификатор модели |
| name | string | - | Название группы/подгруппы |
| img | string/null | - | Ссылка на изображение |
| hasSubgroups | boolean | - | Если истенно, то следующий уровень - группы (появятся изображения) |
| hasParts | boolean | - | Ссылка на изображение |
| parentId | string | Да | ID родительской группы |

#### ВАЖНО! URL для перехода к подгруппам/номерам формируется следующим образом:
- Если есть criteria в GET параметрах - не забываем ее передавать
- Если hasSubgroups то ссылка будет .../:modification/:group.id (+ criteria)
- Если hasParts то ссылка будет .../:modification/:group.parentId/:group.id


### Значения

| Имя точка | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| criteria | string | Да | Критерия для фильтрации групп и подгрупп |
| group | string | - | Если была выбрана какая-либо группа 1-n уровень, здесь будет ее ID |

### Значения model

| Имя точка | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| id | string | - | Идентификатор модели |
| name | string | - | Имя модели |
| img | string | - | Ссылка на изображение |

### Значения modification

| Имя точка | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| id | string | - | Идентификатор модификации |
| name | string | - | Название модификации |
| model.name | string | - | Имя модели |
| model.id | string | - | ID модели |
| transmission.name | string/null | - | Имя трансмиссии |
| transmission.type | string/null | - | Тип трансмиссии |
| engine | string/null | - | Двигатель |
| bodyType | string/null | - | Тип кузова |
| steering | string/null | - | Рулевое управление |
| year | string/null | - | Год выпуска |
| region | string/null | - | Регион |
| description | string/null | - | Описание |

### Значения breadcrumbs

| Имя точка | Тип | Описание |
| :---- | :------: | :--------------- |
| name | string | Имя хлебной крошки |
| url | string | адрес текущей хлебной крошки |


## `GET https://acat.online/api/breadcrumbs[0].url/breadcrumbs[1].url/breadcrumbs[2].url/breadcrumbs[3].url/breadcrumbs[4].url/breadcrumbs[5].url/:subgroup`