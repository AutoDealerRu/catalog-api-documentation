# Поиск по номеру

**Для всех каталогов есть 3 обязательный параметра**

| Имя | Тип | Описание |
| :---- | :------: | :--------------- |
| type | string  | Тип транспортного средства (CARS_NATIVE / CARS_FOREIGN / BUS /  ... ) |
| mark | string | Название марки, в которой ищется номер (VAZ / BMW / KIA / NISSAN / ...) |
| number | string  | Искомый номер (например: '12345') |

**ВАЖНО!**

- для каталога a2d в поле number можно передавать номер детали(текст, например "21116-1000260-00" или "21116100026000")
- поиск по тексту не зависит от регистра, и не учитывает спецсимволы (!"№;%:?*-=_+., )
- результаты в каталогах отличаются
- в любом ответе всегда есть поле mark для определения каталога

## Примеры поиска по номеру в разных каталогах

1. **A2D** [[Запрос](search_numbers.md#Пример-запроса-a2d)] [[Ответ](search_numbers.md#Пример-ответа-a2d)] [[Значения](search_numbers.md#Значения-ответа-a2d)]

### Пример запроса A2D

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/search2?type=CARS_NATIVE&mark=VAZ&number=21116-1000260-00
```
**С уточнением модели**
```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/search2?type=CARS_NATIVE&mark=VAZ&number=8201315743&model=37531
```

#### Пример ответа A2D

```json
[
    {        
        "type": "CARS_NATIVE",
        "mark_short_name": "VAZ",
        "name": "Двигатель в сборе",
        "notes": "",
        "modification": "KSOY5-42 (5-местный универсал)",
        "number": "8201315743",
        "index": "1",
        "id": "21156437",
        "group_short_name": 2085545,
        "model_short_name": 37531,
        "group_name": "Двигатель в сборе (16 кл)",
        "model_name": "Largus",
        "mark_name": "ВАЗ"
    },
    ...
]
```

#### Значения ответа A2D

| Имя точка | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| type | string | Да | Тип транспортного средства |
| mark_short_name | string | Да | Идентификатор марки |
| model_short_name | integer | Да | ID модели |
| group_short_name | integer | Да | ID группы |
| number | string | - | Номер |
| index | integer | - | Порядковый номер |
| id | integer | - | Идентификатор |
| mark_name | string | - | Название марки |
| model_name | string | - | Название модели |
| group_name | string | - | Название группы |
| name | string | - | Название детали |
| modification | string | - | Модифиация |
| notes | string | - | Примечания |

**Для уточнения поиска до модели необходимо передать в запрос ID модели**

[**Пример построения ссылки**](https://github.com/AutoDealerRu/acat-online-example/blob/master/templates/a2d/search.php#L21) на конечную страницу каталога