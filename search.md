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
-X GET https://acat.online/api/catalogs/search?text=ваз
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
-X GET https://acat.online/api/catalogs/search?text=300
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
-X GET https://acat.online/api/catalogs/search?text=00KY6-000001
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
-X GET https://acat.online/api/catalogs/search?text=U5YFF24227L020768
```

### Примеры по каталогам:
1. BMW, Mini, Rolls-Royce [[Ответ](/blob/master/search.md#Пример-ответа-BMW-Mini-Rolls-Royce)] [[Значения](/blob/master/search.md#Значения-ответа-BMW-Mini-Rolls-Royce)]
2. Audi, Seat, Skoda, Volkswagen [[Ответ](/blob/master/search.md#Пример-ответа-Audi-Seat-Skoda-Volkswagen)] [[Значения](/blob/master/search.md#Значения-ответа-Audi-Seat-Skoda-Volkswagen)]
3. Abarth, Alfa Romeo, Fiat, Lancia [[Ответ](/blob/master/search.md#Пример-ответа-Abarth-Alfa-Romeo-Fiat-Lancia)] [[Значения](/blob/master/search.md#Значения-ответа-Abarth-Alfa-Romeo-Fiat-Lancia)]
4. Hyundai, Kia [[Ответ](/blob/master/search.md#Пример-ответа-Hyundai-Kia)] [[Значения](/blob/master/search.md#Значения-ответа-Hyundai-Kia)]
5. Infiniti, Nissan [[Ответ](/blob/master/search.md#Пример-ответа-Infiniti-Nissan)] [[Значения](/blob/master/search.md#Значения-ответа-Infiniti-Nissan)]
6. Lexus, Toyota [[Ответ](/blob/master/search.md#Пример-ответа-Lexus-Toyota)] [[Значения](/blob/master/search.md#Значения-ответа-Lexus-Toyota)]
7. Mercedes Benz, Smart [[Ответ](/blob/master/search.md#Пример-ответа-Lexus-Toyota)] [[Значения](/blob/master/search.md#Значения-ответа-Lexus-Toyota)]

### Пример ответа BMW, Mini, Rolls Royce

```json
{
    "vins": [
        {
            "type": "MOTORCYCLE",
            "mark": "BMW",
            "series_short_name": "K589",
            "model_short_name": 51746,
            "rule_position": "MIDDLE",
            "transmission": "MANUAL",
            "name": "K 100 83 (0501,0511)",
            "market_code": "ECE",
            "market_name": "ЕЭК",
            "series_name": "K589 (K100, RS, RT, LT)",
            "category_short_name": "ohne",
            "catalog_type": "ST"
        },
        ...
    ]
}
```

### Значения ответа BMW, Mini, Rolls Royce

| Имя точка | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| vins[..].type | string | Да | Тип транспортного средства |
| vins[..].mark | string | Да | Сокращенное имя марки |
| vins[..].series_short_name | string | Да | Сокращенное имя серии |
| vins[..].model_short_name | integer | Да | Сокращенное имя серии |
| vins[..].rule_position | string | Да | Сокращенное имя модифиации |
| vins[..].transmission | string | Да | Сокращенное имя модифиации |
| vins[..].name | string | - | Имя Модели |
| vins[..].market_code | string | - | Код страны-производителя |
| vins[..].market_name | string | - | Имя страны-производителя |
| vins[..].series_name | string | - | Имя серии |
| vins[..].category_short_name | string | - | Сокращенное имя категории |
| vins[..].catalog_type | string | - | Тип каталога |

### Пример ответа Audi, Seat, Skoda, Volkswagen

```json
{
    "vins": [
        {
            "vin": "1VWAH7A39CC022903",
            "type": "CARS_FOREIGN",
            "mark": "VOLKSWAGEN",
            "prod_date": "2011-10-25T00:00:00.000Z",
            "model_year": 2012,
            "gearbox": "MAN",
            "country_code": "X9A",
            "pr_nums": [
                "A8B",
                ...
            ],
            "opt02": "062",
            "roof_equipment": "HT",
            "roof_color": "K5",
            "roof_paint": "K5",
            "complectation": {
                "catalog_code": 691,
                "complectation_code": "A322S6",
                "dir": "R",
                "gearbox": {
                    "code": "MAN",
                    "model": "6A",
                    "installation_dates": [
                        {
                            "date_start": "2011-01-01T00:00:00.000Z",
                            "date_end": "2012-04-01T00:00:00.000Z"
                        }
                    ]
                },
                "engine": {
                    "code": "CBT",
                    "volume": "250",
                    "kilowatt": "125",
                    "horsepower": "170",
                    "cylinders": "5",
                    "models": "5S,6A",
                    "installation_dates": [
                        {
                            "date_start": "2011-01-01T00:00:00.000Z",
                            "date_end": null
                        }
                    ]
                },
                "drive_axles": "6A",
                "gearbox_code": "MAN",
                "is_gearbox_info_clear": true,
                "is_axles_info_clear": true,
                "engine_code": "CBTA"
            },
            "models": [
                {
                    "name": "PA",
                    "full_name": "Passat, Passat/4Motion",
                    "countries": [
                        {
                            "short_name": "USA",
                            "full_name": "США"
                        },
                        {
                            "short_name": "MEX",
                            "full_name": "Мексика"
                        }
                    ]
                }
            ],
            "abbreviations": [
                {
                    "number": "A8B",
                    "family": "AUS",
                    "text": "Базовая комплектация",
                    "family_text": "Варианты комплектации"
                },
                ...
            ]
        },
        ...
    ]
}
```

### Значения ответа Audi, Seat, Skoda, Volkswagen

| Имя точка | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| vins | array of objects | - | Номера вин иописание |
| vins[..].vin | string | - | VIN номер |
| vins[..].type | string | Да | Тип транспортного средства |
| vins[..].mark | string | Да | Марка транспортного средства |
| vins[..].complectation.complectation_code | string | - | ID продавца |
| vins[..].complectation.engine_code | string | - | Двигатель (имя) |
| vins[..].complectation.drive_axles | string | - | ID привода осей |
| vins[..].complectation.engine.volume | string | - | Объем, см3 |
| vins[..].complectation.engine.kilowatt | string | - | Мощность, кВт |
| vins[..].complectation.engine.horsepower | string | - | Мощность, л.с. |
| vins[..].complectation.engine.cylinders | string | - | Цилиндров |
| vins[..].complectation.engine.models | string | - | Возможные КП |
| vins[..].complectation.engine.installation_dates[..].date_start | date (string) / null | - | Время монтажа (начало) |
| vins[..].complectation.engine.installation_dates[..].date_end | date (string) / null | - | Время монтажа (начало) |
| vins[..].complectation.gearbox.code | string | - | Обозначение КПП |
| vins[..].complectation.gearbox.model | string | - | ID привода осей |
| vins[..].complectation.gearbox.installation_dates | array | - | Время монтажа |
| vins[..].complectation.gearbox.installation_dates[..].date_start | date (string) / null | - | Время начала монтажа |
| vins[..].complectation.gearbox.installation_dates[..].date_end | date (string) / null | - | Время конца монтажа |
| vins[..].models[..].full_name | string | - | Выбранная модель |

| vins[..].country_code | string | - | Код страны |
| vins[..].prod_date | date(string) | - | Производство |
| vins[..].model_year | integer | - | Модельный год |
| vins[..].complectation.gearbox_code | string | - | КПП |
| vins[..].pr_nums | array of string | - | Список сокращений |
| vins[..].roof_equipment | string | - | Оснащение |
| vins[..].roof_color | string | - | Цвет крыши |
| vins[..].roof_paint | string | - | Цвет кузова |
| abbreviations[..].number | string | - | Номер сокращения |
| abbreviations[..].family | string | - | Семейство сокращения |
| abbreviations[..].text | string | - | Текст сокращения (чаще всего англ) |
| abbreviations[..].family_text | string | - | Семейство текста (чаще русский) |

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

### Пример ответа Hyundai, Kia
**В редких случаях может быть два результата (разные страны)**
```json
{
    "vins": [
        {
            "vin": "U5YFF24227L020768",
            "type": "CARS_FOREIGN",
            "mark": "KIA",
            "country_short": "EUR",
            "family": "CEED",
            "model": "SEURPED06",
            "modification": "BSS6D2615",
            "model_name": "CEED 06 (2006-)"
        },
        ...
    ]
}
```

### Значения ответа Hyundai, Kia

| Имя точка | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| vins[..].vin | string | - | VIN номер |
| vins[..].type | string | Да | Тип транспортного средства |
| vins[..].mark | string | Да | Марка |
| vins[..].country_short | string | Да | Сокращение страны |
| vins[..].family | string | Да | Семейство |
| vins[..].model | string | Да | Номер модели |
| vins[..].modification | integer | Да | Номер модификации |
| vins[..].model_name | string | - | Имя модели |

### Пример ответа Infiniti, Nissan
**В редких случаях может быть два результата (разные страны)**
```json
{
    "vins": [
        {
            "vin": "KNMCSHLMS7P680889",
            "type": "CARS_FOREIGN",
            "mark": "NISSAN",
            "country_short_name": "EL",
            "directory": "016",
            "modification": 4,
            "model_name": "ALMERA B10RS"
        },
        ...
    ]
}
```

### Значения ответа Infiniti, Nissan

| Имя точка | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| vins[..].vin | string | - | VIN номер |
| vins[..].type | string | Да | Тип транспортного средства |
| vins[..].mark | string | Да | Марка транспортного средства |
| vins[..].country_short_name | string | Да | Сокращение страны |
| vins[..].directory | string | Да | Сокращенный номер модели |
| vins[..].modification | integer | Да | Номер модификации |
| vins[..].model_name | string | - | Имя модели с серией |

### Пример ответа Lexus, Toyota

```json
{
    "vins": [
        {
            "vin": "JTEHF21A**0076044",
            "type": "CARS_FOREIGN",
            "mark": "TOYOTA",
            "country_short_name": "US",
            "catalog_code": "522410",
            "model_code": "MCU25L-BWPNKA",
            "sysopt": "sysopt",
            "complectation_code": "004"
        },
        ...
    ]
}
```

### Значения ответа Lexus, Toyota

| Имя точка | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| vins[..].vin | string | - | VIN номер |
| vins[..].type | string | Да | Тип транспортного средства |
| vins[..].mark | string | Да | Марка транспортного средства |
| vins[..].country_short_name | string | Да | Сокращение страны |
| vins[..].catalog_code | string | Да | Код каталога |
| vins[..].model_code | integer | Да | Код модели |
| vins[..].sysopt | integer | Да | - |
| vins[..].complectation_code | integer | Да | Код комплектации |

### Пример ответа Mercedes Benz, Smart
**В редких случаях может быть два результата (разные страны)**
```json
{
    "vins": [
        {
            "type": "CARS_FOREIGN",
            "mark": "MERCEDES_BENZ",
            "country": "EU",
            "aggregation": "FG",
            "model": "124043",
            "catalog": "508",
            "name": "PASSSENGER CAR,COUPE UP TO IDENT NO. B 065853 EXCEPT FOR B 014528,B 016676,B 016766,B 022474",
            "modification": "230 CE"
        },
        {
            "type": "CARS_FOREIGN",
            "mark": "MERCEDES_BENZ",
            "country": "EU",
            "aggregation": "FG",
            "model": "124043",
            "catalog": "15T",
            "name": "PASSSENGER CAR,COUPE FROM IDENT NO. B 065854 ALSO INSTALLED ON B 014528,B 016676,B 016766,B 022474",
            "modification": "230 CE"
        }
    ]
}
```

### Значения ответа Mercedes Benz, Smart

| Имя точка | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| vins[..].type | string | Да | Тип транспортного средства |
| vins[..].mark | string | Да | Марка транспортного средства |
| vins[..].country | string | Да | Сокращение страны |
| vins[..].aggregation | string | Да | Сокращение страны |
| vins[..].model | string | Да | Сокращение страны |
| vins[..].catalog | string | Да | Сокращение страны |
| vins[..].name | string | - | Информация о модели |
| vins[..].modification | integer | Да | Имя модели |
