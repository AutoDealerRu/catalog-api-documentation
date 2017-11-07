# Поиск по номеру

**Для всех каталогов есть 3 обязательный параметра**

| Имя | Тип | Описание |
| :---- | :------: | :--------------- |
| type | string  | Тип транспортного средства (CARS_NATIVE / CARS_FOREIGN / BUS /  ... ) |
| mark | string | Название марки, в которой ищется номер (VAZ / BMW / KIA / NISSAN / ...) |
| number | string  | Искомый номер (например: '12345') |
**ВАЖНО!**
- для каталога a2d в поле number можно передавать названия детали(текст, например "кранштейн")
- поиск по тексту не зависит от регистра
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

### Пример запроса A2D

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/search?type=CARS_NATIVE&mark=VAZ&number=Шайба
```
**С уточнением модели**
```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/search?type=CARS_NATIVE&mark=VAZ&number=Шайба&model=37531
```

#### Пример ответа A2D

```json
[
    {
        "type": "CARS_NATIVE",
        "mark_short_name": "VAZ",
        "model_short_name": 37534,
        "group_short_name": 2085644,
        "number": "7701474784",
        "mark_name": "ВАЗ",
        "model_name": "Largus",
        "group_name": "Вал вторичный КПП",
        "name": "Комплект регулировочных шайб",
        "modification": "FS015-40 (5-дверный 2-местный фургон)",
        "notes": "",
        "sort_weight": 30 
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
| sort_weight | integer | - | На сколько подходит под условия поиска (чем больше число - тем больше подходит) |

**Для уточнения поиска до модели необходимо передать в запрос ID модели**

**Для отсеивания "ненужных" результатов можно смотреть на вес первого и оставить из всех результатов только те, у кого вес как у первого элемента**


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



### Пример запроса Toyota,Lexus

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/search?type=CARS_FOREIGN&mark=TOYOTA&number=9165140816&country=US&model=791420
```

#### Пример ответа Toyota,Lexus

```json
[
    {
        ...
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