# Поиск

**Поиск - глобальный, ищет по всем каталогам**

1. [Поиск по номеру](search_numbers.md#Поиск-по-номеру)
2. [Поиск по VIN](search.md#Поиск-по-vin)
3. [Поиск по кузову (frame / фрейму)](search.md#Поиск-по-кузову)
4. [Поиск по модели](search.md#Поиск-по-модели)
5. [Поиск по марке](search.md#Поиск-по-марке)

## Поиск по марке 

### Пример запроса поиска по марке

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/search2?text=ваз
```

### Пример ответа поиска по марке

```json
{
    "marks" : [
        {
            "mark_name": "VAZ_ARCHIVE",
            "breadcrumbs": [
                {
                    "name": "Легковые (отечественные)",
                    "url": "CARS_NATIVE"
                },
                {
                    "name": "ВАЗ Архивный",
                    "url": "VAZ_ARCHIVE"
                }
            ]
        },{
            "mark_name": "VAZ",
            "breadcrumbs": [
                {
                    "name": "Легковые (отечественные)",
                    "url": "CARS_NATIVE"
                },
                {
                    "name": "ВАЗ",
                    "url": "VAZ"
                }
            ]
        }
    ]
}
```

### Значения поиска по марке

| Имя точка | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| marks[..].mark_name | string | - | Тип транспортного средства |
| marks[..].breadcrumbs[..].name | string | - | Название |
| marks[..].breadcrumbs[..].url | string | Да | URL параметр |



## Поиск по модели

### Пример запроса поиска по модели

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/search2?text=300
```

### Пример ответа поиска по модели

```json
{
    "marks" : [
        {
            "mark_name": "KAMAZ",
            "model_name": "65115",
            "property": "65115 - автомобиль-самосвал (6x4); 65115-0006056-А4, 65115-0006057-А4, 65115-0006058-А4, 65115-0006059-А4; Cummins 6ISBe4 300 (Euro-4) (023.08.2012)",
            "breadcrumbs": [
                {
                    "name": "Грузовые (отечественные)",
                    "url": "TRUCKS_NATIVE"
                },
                {
                    "name": "КамАЗ",
                    "url": "KAMAZ"
                },
                {
                    "name": "65115",
                    "url": "54287"
                }
            ]
        },
        ...,
        {
            "mark_name": "MERCEDES_BENZ_SKD",
            "model_name": "E 300 T CDI DPF BlueEFFICIENCY Avantgarde 7G-Tronic",
            "property": "Двигатель: Д/3,0/150Kw  Кузов: универсал  Серия: E-класс (S212)",
            "breadcrumbs": [
                {
                    "name": "Легковые (иномарки)",
                    "url": "CARS_FOREIGN"
                },
                {
                    "name": "Mercedes Benz",
                    "url": "MERCEDES_BENZ_SKD"
                },
                {
                    "name": "E 300 T CDI DPF BlueEFFICIENCY Avantgarde 7G-Tronic",
                    "url": "53278"
                }
            ]
        },
        ...,
        {
            "mark_name": "BMW",
            "model_name": "300",
            "property": "Седан США 300",
            "breadcrumbs": [
                {
                    "name": "Легковые (иномарки)",
                    "url": "CARS_FOREIGN"
                },
                {
                    "name": "BMW",
                    "url": "BMW"
                },
                {
                    "name": "Isetta",
                    "url": "ISE"
                }
            ],
            "queries": {
                "short_name": 47816
            },
        }
    ]
}
```
**В ответе будут содержатся все модели у которых содержится в тексте модификации / модели искомое значение**
**Для фильтрации по марке первым словом (словами) можно передать марку, например "бмв 300" и в результатах будут только модели марки бмв**

### Значения поиска по модели

| Имя точка | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| marks[..].mark_name | string | - | Тип транспортного средства |
| marks[..].model_name | string | - | Имя модели |
| marks[..].property | string | - | Свойства (модификация, период выпуска, страна и т.д. содержася в этой строке) |
| marks[..].breadcrumbs[..].name | string | - | Название |
| marks[..].breadcrumbs[..].url | string | Да | URL параметр |
| marks[..].queries | object | - | Доп. URL параметр |
| marks[..].queries.key | string | - | Имя параметра, дописываемого к URL модели (на примере BMW: .../ISE?short_name=47816) |
| marks[..].queries.value | string | - | Имя параметра, дописываемого к URL модели (на примере BMW: .../ISE?short_name=47816) |



## Поиск по кузову

### Пример запроса поиска по кузову
**Правила кузова: тире обязательно, до тире 3-6 символов(буквы латиницы/цифры), после тире 6-7 цифр**
```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/search2?text=00KY6-000001
```

### Пример ответа поиска по кузову Nissan

```json
{
    "frames": [
        {
            "type": "CARS_FOREIGN",
            "mark": "NISSAN",
            "country_short_name": "AR",
            "directory": "321",
            "modification": 2,
            "model_name": "SAFARI Y60"
        },
        ...
    ]
}
```

### Значения поиска по кузову Nissan

| Имя точка | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| frames | array of objects | - | Результаты поиска по кузову |
| frames[..].type | string | Да | Тип транспортного средства |
| frames[..].mark | string | Да | Марка транспортного средства |
| frames[..].country_short_name | string | Да | Сокращение страны |
| frames[..].directory | string | Да | Сокращенный номер модели |
| frames[..].modification | integer | Да | Номер модификации |
| frames[..].model_name | string | - | Модели с модификацией |

### Пример ответа поиска по кузову Toyota/Lexus

```json
{
    "frames": [
        {
            "type": "CARS_FOREIGN",
            "mark": "TOYOTA",
            "country_short_name": "JP",
            "catalog_code": "662120",
            "model_code": "ACA20W-AZPSH",
            "sysopt": "sysopt",
            "complectation_code": "006",
            "model_name": "RAV4 J/L"
        },
        ...
    ]
}
```

### Значения поиска по кузову Toyota/Lexus

| Имя точка | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| frames | array | - | Результаты поиска по кузову |
| frames[..].type | string | Да | Тип транспортного средства |
| frames[..].mark | string | Да | Марка транспортного средства |
| frames[..].country_short_name | string | Да | Сокращение страны |
| frames[..].catalog_code | string | Да | Сокращенный номер каталога |
| frames[..].model_code | string | Да | Сокращенный номер модели |
| frames[..].sysopt | string | Да | - |
| frames[..].complectation_code | string | Да | Номер комплектации |
| frames[..].model_name | string | - | Модели с модификацией |



## Поиск по VIN
**Результаты для каждого из каталогов немного отличаются**
**Для определения каталога используйте vins[..].mark**

### Пример запроса

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/search2?text=U5YFF24227L020768
```

#### Пример запроса с указанием марки

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/search2?text=U5YFF24227L020768&catalog=PARTS&mark=kia
``` 

1. Доступные каталоги для поиска по VIN: FIAT, PARTS
2. Доступные марки можно посмотреть по [[ссылке](https://acat.online/api/public/types)]

Например у каталога FIAT:
```
"marks": [ "FIAT", "LANCIA", "ALFA_ROMEO", "ABARTH" ]
```


### Примеры по каталогам:
1. Abarth, Alfa Romeo, Fiat, Lancia [[Ответ](search.md#Пример-ответа-abarth-alfa-romeo-fiat-lancia)] [[Значения](search.md#Значения-ответа-abarth-alfa-romeo-fiat-lancia)]
2. Parts (остальные с отметкой поиска по VIN) [[Ответ](search.md#Пример-ответа-parts)] [[Значения](search.md#Значения-ответа-parts)]

### Пример ответа Abarth, Alfa Romeo, Fiat, Lancia

```json
{
    "vins": [
        {
            "vin": "323B3118594",
            "type": "CARS_FOREIGN",
            "mark": "FIAT",
            "model_short_name": "LIN",
            "modification_short_name": "3M",
            "modification_name": "LINEA (2007-....)"
        },
        ...
    ]
}
```

### Значения ответа Abarth, Alfa Romeo, Fiat, Lancia

| Имя точка | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| vins[..].vin | string | - | VIN номер |
| vins[..].type | string | Да | Тип транспортного средства |
| vins[..].mark_short_name | string | Да | Марка |
| vins[..].model_short_name | string | Да | Сокращенное имя модели |
| vins[..].modification_short_name | string | Да | Сокращенное имя модифиации |
| vins[..].modification_name | string | - | Имя модификации |

### Пример ответа Parts
**В редких случаях может быть два результата (разные страны)**
```json
{
    "vins": [
        {
            "type": "CARS_FOREIGN",
            "mark": "mitsubishi",
            "markName": "Mitsubishi",
            "model": "46540d9181d08100272d2e844a7a5cd1",
            "modelName": "Colt / Lancer / Mirage / Space Star",
            "modification": "201fa6542d8785154453f778f386435c",
            "parameters": [
                {
                    "value": "1600(SEDAN)",
                    "name": "Car parameters"
                },
                {
                    "value": "CS3A",
                    "name": "Modification"
                },
                {
                    "value": "2007",
                    "name": "Year"
                },
                {
                    "value": "Europe",
                    "name": "Region"
                },
                {
                    "value": "Left hand",
                    "name": "Steering"
                }
            ],
            "optionCodes": [
                {
                    "code": "L",
                    "description": "Left Hand"
                },
                ...
            ],
            "criteria": "51*JMBSNCS3A7U022230~2007021$2000121}2011033^T54A<02P",
            "title": "LANCER/LANCER CLASSIC(EUR)"
        }
    ]
}
```

### Значения ответа Parts

| Имя точка | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| vins[..].type | string | Да | Тип транспортного средства |
| vins[..].mark | string | Да | Марка транспортного средства |
| vins[..].markName | string | - | Название марки |
| vins[..].model | string | Да | ID модели |
| vins[..].modelName | string | - | Имя модели (из каталога) |
| vins[..].modification | string | Да | ID модификации |
| vins[..].parameters | object[] | - | Параметры |
| vins[..].parameters[..].name | string | - | Название параметра |
| vins[..].parameters[..].value | string | - | Значение параметра |
| vins[..].optionCodes | object[] | - | Опционные коды |
| vins[..].optionCodes[..].code | string | - | Код |
| vins[..].optionCodes[..].description | string | - | Расшифровка |
| vins[..].criteria | string | Да | Критерия (для фильтрации групп/номеров) |
| vins[..].title | integer | - | Имя модели (из VIN справочника) |

#### **ВАЖНО!** ссылку формируем https://acat.online/api/catalogs/:type/:mark/:model/:modification?criteria=:criteria
