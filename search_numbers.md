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
2. **Abarth,Alfa-Romeo,Fiat,Lancia** [[Запрос](search_numbers.md#Пример-запроса-abarthalfa-romeofiatlancia)] [[Ответ](search_numbers.md#Пример-ответа-abarthalfa-romeofiatlancia)] [[Значения](search_numbers.md#Значения-ответа-abarthalfa-romeofiatlancia)]
3. **Audi,Seat,Skoda,Volkswagen** [[Запрос](search_numbers.md#Пример-запроса-audiseatskodavolkswagen)] [[Ответ](search_numbers.md#Пример-ответа-audiseatskodavolkswagen)] [[Значения](search_numbers.md#Значения-ответа-audiseatskodavolkswagen)]
4. **BMW,Mini,Rolls-Royce** [[Запрос](search_numbers.md#Пример-запроса-bmwminirolls-royce)] [[Ответ](search_numbers.md#Пример-ответа-bmwminirolls-royce)] [[Значения](search_numbers.md#Значения-ответа-bmwminirolls-royce)]
5. **Kia,Hyundai** [[Запрос](search_numbers.md#Пример-запроса-kiahyundai)] [[Ответ](search_numbers.md#Пример-ответа-kiahyundai)] [[Значения](search_numbers.md#Значения-ответа-kiahyundai)]
6. **Nissan,Infiniti** [[Запрос](search_numbers.md#Пример-запроса-nissaninfiniti)] [[Ответ](search_numbers.md#Пример-ответа-nissaninfiniti)] [[Значения](search_numbers.md#Значения-ответа-nissaninfiniti)]
7. **Dacia,Renault** [[Запрос](search_numbers.md#Пример-запроса-daciarenault)] [[Ответ](search_numbers.md#Пример-ответа-daciarenault)] [[Значения](search_numbers.md#Значения-ответа-daciarenault)]
8. **Toyota,Lexus** [[Запрос](search_numbers.md#Пример-запроса-toyotalexus)] [[Ответ](search_numbers.md#Пример-ответа-toyotalexus)] [[Значения](search_numbers.md#Значения-ответа-toyotalexus)]
9. **Mercedes,Smart** [[Запрос](search_numbers.md#Пример-запроса-mercedessmart)] [[Ответ](search_numbers.md#Пример-ответа-mercedessmart)] [[Значения](search_numbers.md#Значения-ответа-mercedessmart)]
10. **Ssangyong** [[Запрос](search_numbers.md#Пример-запроса-ssangyong)] [[Ответ](search_numbers.md#Пример-ответа-ssangyong)] [[Значения](search_numbers.md#Значения-ответа-ssangyong)]

### Пример запроса A2D

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/search?type=CARS_NATIVE&mark=VAZ&number=21116-1000260-00
```
**С уточнением модели**
```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/search?type=CARS_NATIVE&mark=VAZ&number=8201315743&model=37531
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
| mark_name | string | - | Название марки |
| model_name | string | - | Название модели |
| group_name | string | - | Название группы |
| name | string | - | Название детали |
| modification | string | - | Модифиация |
| notes | string | - | Примечания |

**Для уточнения поиска до модели необходимо передать в запрос ID модели**

[**Пример построения ссылки**](https://github.com/AutoDealerRu/acat-online-example/blob/master/templates/a2d/search.php#L21) на конечную страницу каталога


### Пример запроса Abarth,Alfa-Romeo,Fiat,Lancia

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/search?type=CARS_FOREIGN&mark=FIAT&number=71740648
```

#### Пример ответа Abarth,Alfa-Romeo,Fiat,Lancia

```json
[
    {
        "type": "CARS_FOREIGN",
        "mark": "FIAT",
        "model": "CIN",
        "modification": "3P",
        "unit": 101,
        "subgroup": "10101/08",
        "variant": 1,
        "number": "71740648",
        "model_name": "PUNTO",
        "modification_name": "PUNTO MY 2013 (2013-....)",
        "unit_name": "БЛОК И ГОЛОВКА ЦИЛИНДРОВ",
        "group_name": "БЛОК И ГОЛОВКА ЦИЛИНДРОВ",
        "subgroup_name": "CYLINDER HEAD AND GASKETS",
        "number_name": "CYLINDER HEAD WITH VALVES"
    },
    ...
]
```

#### Значения ответа Abarth,Alfa-Romeo,Fiat,Lancia

| Имя точка | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| type | string | Да | Тип транспортного средства |
| mark | string | Да | Идентификатор марки |
| model | string | Да | Идентификатор модели |
| modification | string | Да | Идентификатор модификации |
| unit | integer | Да | Идентификатор группы |
| subgroup | string | Да | Идентификатор подгруппы |
| variant | integer | Да | Номер варианта изображения |
| number | string | - | Номер |
| model_name | string | - | Название модели |
| modification_name | string | - | Название модификации |
| unit_name | string | - | Название блока |
| group_name | string | - | Название группы |
| subgroup_name | string | - | Название подгруппы |
| number_name | string | - | Название детали |

[**Пример построения ссылки**](https://github.com/AutoDealerRu/acat-online-example/blob/master/templates/fiat/search.php#L21) на конечную страницу каталога


### Пример запроса Audi,Seat,Skoda,Volkswagen

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/search?type=CARS_FOREIGN&mark=AUDI&number=4A0713105
```

#### Пример ответа Audi,Seat,Skoda,Volkswagen

```json
[
    {
        "type": "CARS_FOREIGN",
        "mark": "AUDI",
        "country": "USA",
        "model": "A10",
        "year": 1992,
        "catalog_code": 118,
        "dir": "R",
        "group": "group"
        "group_id": "7",
        "subgroup": "713",
        "detail": 713010,
        "number": "4A0 713 105",
        "country_name": "США",
        "model_full_name": "Audi 100",
        "group_name": "Механизмы переключения, педали",
        "subgroup_names": [
            {
                "name": "Механизм переключения",
                "option": "АКПП"
            },
            ...
        ],
        "number_name": "Кронштйен рычага перек. перед."
    },
    ...
]
```

#### Значения ответа Audi,Seat,Skoda,Volkswagen

| Имя точка | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| type | string | Да | Тип транспортного средства |
| mark | string | Да | Идентификатор марки |
| country | string | Да | Страна |
| model | string | Да | Идентификатор модели |
| year | integer | Да | Год выпуска |
| catalog_code | integer | Да | Код каталога |
| dir | string | Да | Директория |
| group | string | Да | Сервисный номер или обычный |
| group_id | string | Да | Идентификатор группы |
| subgroup | string | Да | Идентификатор подгруппы |
| detail | string | Да | Этой переменной нет где group="service" |
| number | string | - | Номер |
| country_name | string | - | Название страны |
| model_full_name | string | - | Название модели |
| modification_name | string | - | Название модификации |
| group_name | string | - | Название группы |
| subgroup_names | array | - | Массив имен подгрупп |
| subgroup_names[..].name | string | - | Имя подгруппы |
| subgroup_names[..].option | string | - | Опции подгруппы |
| number_name | string | - | Название детали |

**1. Где group=service параметр detail отсутствует и он не нужен**

**2. Имена подгрупп отличаются, но данные на странице результатов одинаковы**

[**Пример построения ссылки**](https://github.com/AutoDealerRu/acat-online-example/blob/master/templates/etka/search.php#L21) на конечную страницу каталога


### Пример запроса BMW,Mini,Rolls-Royce

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/search?type=CARS_FOREIGN&mark=BMW&number=65902352233
```
**С уточнением модели**
```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/search?type=CARS_FOREIGN&mark=BMW&number=65902352233&model=47789
```

#### Пример ответа BMW,Mini,Rolls-Royce

```json
[
    {
        "type": "CARS_FOREIGN",
        "mark": "BMW",
        "series": "E83",
        "model": 47789,
        "rule": "LEFT",
        "transmission": "MANUAL",
        "group": "84",
        "subgroup": 436625,
        "number": "65 90 2352233",
        "series_name": "X3 E83",
        "country_name": "ЕЭК",
        "model_name": "X3 2.0d",
        "group_name": "Системы связи",
        "subgroup_name": "Система Click & Drive BMW",
        "number_name": "Блок на клеевой основе"
    },
    ...
]
```

#### Значения ответа BMW,Mini,Rolls-Royce

| Имя точка | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| type | string | Да | Тип транспортного средства |
| mark | string | Да | Идентификатор марки |
| series | string | Да | Серия |
| model | integer | Да | Идентификатор модели |
| rule | string | Да | Положение руля |
| transmission | string | Да | Трансмиссия |
| group | string | Да | Идентификатор группы |
| subgroup | integer | Да | Идентификатор подгруппы |
| number | string | - | Номер детали (артикул) |
| series_name | string | - | Имя серии |
| country_name | string | - | Название страны |
| model_name | string | - | Название модели |
| group_name | string | - | Название группы |
| subgroup_name | string | - | Название подгруппы |
| number_name | string | - | Название детали |

**На поиск без уточнения по ID модели стоит ограничение в 100 результатов**

[**Пример построения ссылки**](https://github.com/AutoDealerRu/acat-online-example/blob/master/templates/bmw/search.php#L22) на конечную страницу каталога


### Пример запроса Kia,Hyundai

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/search?type=CARS_FOREIGN&mark=KIA&number=646274D310
```
**С уточнением модели**
```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/search?type=CARS_FOREIGN&mark=KIA&number=646274D310&model=EURK4D005A
```

#### Пример ответа Kia,Hyundai

```json
[
    {
        "type": "CARS_FOREIGN",
        "mark": "KIA",
        "country": "EUR",
        "family": "CARNIVAL",
        "model": "EURK4D005A",
        "modification": "GBBD285",
        "group": "BO",
        "subgroup": "6061211",
        "number": "646274D310",
        "model_name": "CARNIVAL/SEDONA 05: -OCT.2006 (2006-2006)",
        "modification_info": {
            "body": "WGN SHORT 7",
            "class": "MIDDLE GRADE",
            "engine_displacement": "2900 CC",
            "fuel": "T/C INTER COOLER",
            "transmission": "5 SPEED MT 2WD"
        },
        "group_name": "Кузовная",
        "subgroup_name": "60-612 Подкрылок и панель крепления радиатора",
        "number_name": "REINF ASSY-RR SIDE MEMBER RH"
    },
    ...
]
```

#### Значения ответа Kia,Hyundai

| Имя точка | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| type | string | Да | Тип транспортного средства |
| mark | string | Да | Идентификатор марки |
| country | string | Да | Идентификатор страны |
| family | string | Да | Семейство |
| model | string | Да | Идентификатор модели |
| modification | string | Да | Идентификатор модификации |
| group | string | Да | Идентификатор группы |
| subgroup | string | Да | Идентификатор подгруппы |
| number | string | - | Номер детали (артикул) |
| model_name | string | - | Название модели |
| modification_info | object | - | Информация о модификации |
| modification_info.body | string | - | Кузов |
| modification_info.class | string | - | Класс |
| modification_info.engine_displacement | string | - | Рабочий обьем двигателя |
| modification_info.fuel | string | - | Топливо |
| modification_info.transmission | string | - | Трансмиссия |
| group_name | string | - | Название группы |
| subgroup_name | string | - | Название подгруппы |
| number_name | string | - | Название детали |

[**Пример построения ссылки**](https://github.com/AutoDealerRu/acat-online-example/blob/master/templates/kia/search.php#L21) на конечную страницу каталога


### Пример запроса Nissan,Infiniti

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/search?type=CARS_FOREIGN&mark=NISSAN&number=14713VK500
```
**С уточнением страны**
```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/search?type=CARS_FOREIGN&mark=NISSAN&number=14713VK500&country=EL
```
**С уточнением страны и модели**
```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/search?type=CARS_FOREIGN&mark=NISSAN&number=14713VK500&country=EL&model=030
```

#### Пример ответа Nissan,Infiniti

```json
[
    {
        "type": "CARS_FOREIGN",
        "mark": "NISSAN",
        "country": "EL",
        "model": "014",
        "modification": 2,
        "group": "A",
        "subgroup": "147",
        "figure": "147A",
        "section": "001",
        "number": "14713",
        "subnumber": "14713VK500",
        "country_name": "Европа (лев)",
        "model_name": "HARDBODY",
        "model_serial": "D22S",
        "modification_name": {
            "engine": "YD25DDTI",
            "body": "SC",
            "drive": "2WD",
            "transmission": "MT"
        },
        "group_name": "ENGINE MECHANICAL",
        "subgroup_name": "EGR PARTS",
        "number_name": "GUIDE TUBE-EGR"
    },
    ...
]
```

#### Значения ответа Nissan,Infiniti

| Имя точка | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| type | string | Да | Тип транспортного средства |
| mark | string | Да | Идентификатор марки |
| country | string | Да | Идентификатор страны |
| model | string | Да | Идентификатор модели |
| modification | integer | Да | Идентификатор модификации |
| group | string | Да | Идентификатор группы |
| subgroup | string | Да | Идентификатор подгруппы |
| figure | string | Да | Номер фигуры на изображении |
| section | string | Да | Номер изображения |
| number | string | - | Номер детали (артикул) |
| subnumber | null/string | - | Номер детали (артикул, бывает что это "подномер" на изображении) |
| model_name | string | - | Название модели |
| model_serial | string | - | Название серии |
| modification_name | object | - | Информация о модификации |
| modification_name.engine | null/string | - | Двигатель |
| modification_name.body | null/string | - | Кузов |
| modification_name.drive | null/string | - | Привод |
| modification_name.transmission | null/string | - | Трансмиссия |
| group_name | string | - | Название группы |
| subgroup_name | string | - | Название подгруппы |
| number_name | string | - | Название детали |

[**Пример построения ссылки**](https://github.com/AutoDealerRu/acat-online-example/blob/master/templates/nissan/search.php#L21) на конечную страницу каталога


### Пример запроса Dacia,Renault

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/search?type=CARS_FOREIGN&mark=RENAULT&number=600503272R
```
**С уточнением модели**
```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/search?type=CARS_FOREIGN&mark=RENAULT&number=600503272R&model=7
```

#### Пример ответа Dacia,Renault

```json
[
    {
        "subgroup_short_name": 28051,
        "type": "CARS_FOREIGN",
        "mark": "RENAULT",
        "model": 7,
        "modification": 159,
        "category": 476,
        "category_name": "Кузов",
        "modification_name": "BB00",
        "model_name": "Clio II",
        "mark_name": "Renault"
    },
  ...
]
```

#### Значения ответа Dacia,Renault

| Имя точка | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| type | string | Да | Тип транспортного средства |
| mark | string | Да | Идентификатор марки |
| model | string | Да | Идентификатор модели |
| modification | integer | Да | Идентификатор модификации |
| category | string | Да | Идентификатор категории |
| category_name | string | Да | Наименование категории |
| modification_name | string | Да | Наименование модификации |
| model_name | string | Да | Наименование модели |
| mark_name | string | - | Наименование марки |
| subgroup_short_name | string | - | Идентификатор подгруппы |

[**Пример построения ссылки**](https://github.com/AutoDealerRu/acat-online-example/blob/master/templates/renault/search.php#L20) на конечную страницу каталога



### Пример запроса Toyota,Lexus

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/search?type=CARS_FOREIGN&mark=TOYOTA&number=9165140816&country=US&model=791420
```

#### Пример ответа Toyota,Lexus

```json
[
    {
        "type": "CARS_FOREIGN",
        "mark": "TOYOTA",
        "country": "US",
        "catalog_code": "791420",
        "model_code": "FJ60LG-KA",
        "sysopt": "sysopt",
        "complectation_code": "004",
        "group": "1603",
        "illustration": "MA4986K",
        "number": "9165140816",
        "country_name": "США",
        "model_name": "LAND CRUISER",
        "model_modification": "BJ60,HJ60,FJ6#",
        "complectation_name": "FJ60LG-KA",
        "group_name": "RADIATOR & WATER OUTLET",
        "number_name": "** STANDARD PART"
    },
    ...
]
```

#### Значения ответа Toyota,Lexus

| Имя точка | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| type | string | Да | Тип транспортного средства |
| mark | string | Да | Идентификатор марки |
| country | string | Да | Идентификатор страны |
| catalog_code | string | Да | Код каталога |
| model_code | integer | Да | Код модели |
| sysopt | integer | Да | - |
| complectation_code | integer | Да | Код комплектации |
| group | string | Да | Идентификатор группы |
| illustration | string | Да | Идентификатор подгруппы (изображения) |
| number | string | - | Номер детали (артикул) |
| subnumber | null/string | - | Номер детали (артикул, бывает что это "подномер" на изображении) |
| country_name | string | - | Название страны |
| model_name | string | - | Название модели |
| model_modification | string | - | Название модификаций |
| complectation_name | object | - | Информация о комплектации |
| group_name | string | - | Название группы |
| number_name | string | - | Название детали |

[**Пример построения ссылки**](https://github.com/AutoDealerRu/acat-online-example/blob/master/templates/toyota/search.php#L21) на конечную страницу каталога


### Пример запроса Mercedes,Smart

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/search?type=CARS_FOREIGN&mark=MERCEDES_BENZ&number=A1242601798
```

**С уточнением страны**
```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/search?type=CARS_FOREIGN&mark=MERCEDES_BENZ&number=A1242601798&country=EU
```

**С уточнением страны и модели**
```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/search?type=CARS_FOREIGN&mark=MERCEDES_BENZ&number=A1242601798&country=EU&model=201024
```

#### Пример ответа Mercedes,Smart

```json
[
    {
        "type": "CARS_FOREIGN",
        "mark": "MERCEDES_BENZ",
        "country": "EU",
        "aggregation": "FG",
        "model": "201024",
        "catalog": "14A",
        "group": "26",
        "subgroup": "030",
        "country_name": "Европа",
        "aggregation_name": "Шасси",
        "model_name": "190 E AUSTRALIA",
        "group_name": "ПЕРЕКЛЮЧЕНИЕ",
        "subgroup_name": "FLOOR SHIFT USED WITH MANUAL FIVESPEED TRANSMISSION",
        "name": "ПРИВОД КП НА ЦЕНТР. КОНС.",
        "description": "FOUR-GATE SHIFT"
    },
    ...
]
```

#### Значения ответа Mercedes,Smart

| Имя точка | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| type | string | Да | Тип транспортного средства |
| mark | string | Да | Идентификатор марки |
| country | string | Да | Идентификатор страны |
| aggregation | string | Да | Тип аггрегата |
| model | integer | Да | Код модели |
| catalog | integer | Да | Идентификатор каталога |
| group | string | Да | Идентификатор группы |
| subgroup | string | Да | Идентификатор подгруппы |
| sa_id | not exist/string | Да | Идентификатор SA |
| stroke_id | not exist/string | Да | Идентификатор STROKE |
| number | string | - | Номер детали (артикул) |
| subnumber | null/string | - | Номер детали (артикул, бывает что это "подномер" на изображении) |
| country_name | string | - | Название страны |
| aggregation_name | string | - | Название аггрегата |
| model_name | string | - | Название модели |
| group_name | string | - | Название группы |
| subgroup_name | string | - | Название подгруппы |
| number_name | string | - | Название детали |

**На поиск без уточнения по ID модели стоит ограничение в 100 результатов**

[**Пример построения ссылки**](https://github.com/AutoDealerRu/acat-online-example/blob/master/templates/mercedes/search.php#L21) на конечную страницу каталога


### Пример запроса Ssangyong

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/search?type=CARS_FOREIGN&mark=SSANGYONG&number=6011108000
```

#### Пример ответа Ssangyong

```json
[
    {
        "model": 389410638,
        "group": 1633727457,
        "subgroup": 1888337408,
        "model_name": "Actyon",
        "group_name": "Body",
        "subgroup_name": "BODY MOUNTING",
        "number": "6011108000",
        "number_name": "INSULATOR-BODY NO1 UPR"
    },
    ...
]
```

#### Значения ответа Ssangyong

| Имя точка | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| type | string | Да | Всегда 'CARS_FOREIGN' (дополнить при составлении URL адреса) |
| mark | string | Да | Всегда 'SSANGYONG' (дополнить при составлении URL адреса) |
| model | number | Да | Код модели |
| group | number | - | Идентификатор группы |
| subgroup | number | Да | Идентификатор подгруппы |
| number | string | - | Номер детали (артикул) |
| model_name | string | - | Название модели |
| group_name | string | - | Название группы |
| subgroup_name | string | - | Название подгруппы |
| number | string | - | Номер (артикул) |
| number_name | string | - | Название детали |

[**Пример построения ссылки**](https://github.com/AutoDealerRu/acat-online-example/blob/master/templates/ssangyong/search.php#L21) на конечную страницу каталога
