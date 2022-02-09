# Поиск

**Поиск - глобальный, ищет по всем каталогам**

1. [Поиск по номеру](search_numbers.md#Поиск-по-номеру)
2. [Поиск по VIN/Frame(кузову)](search.md#Поиск-по-vin)
3. [Поиск по модели](search.md#Поиск-по-модели)
4. [Поиск по марке](search.md#Поиск-по-марке)

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



## Поиск по VIN

### Пример запроса

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/search2?text=U5YFF24227L020768
```

### Пример запроса с указанием марки

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/search2?text=U5YFF24227L020768&catalog=PARTS&mark=kia
```

### Пример ответа
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
            "modelImg": "https://img2.acat.online/models/mitsubishi/Colt_Lancer_Mirage_Space-Star.jpg",
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
            "criteriaURI": "b6%2AJMBSNC62AKU467010~1988113!c16f6b53%241988041%7D1995073%5EWB9+%3C27H%3EU09",
            "title": "LANCER/LANCER CLASSIC(EUR)"
        }
    ]
}
```

### Значения ответа

| Имя точка | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| vins[..].type | string | Да | Тип транспортного средства |
| vins[..].mark | string | Да | Марка транспортного средства |
| vins[..].markName | string | - | Название марки |
| vins[..].model | string | Да | ID модели |
| vins[..].modelName | string/null | - | Имя модели (из каталога) |
| vins[..].modelImg | string/null | - | Изображение модели |
| vins[..].modification | string | Да | ID модификации |
| vins[..].parameters | object[] | - | Параметры |
| vins[..].parameters[..].name | string | - | Название параметра |
| vins[..].parameters[..].value | string | - | Значение параметра |
| vins[..].optionCodes | object[] | - | Опционные коды |
| vins[..].optionCodes[..].code | string | - | Код |
| vins[..].optionCodes[..].description | string | - | Расшифровка |
| vins[..].criteria | string | - | Критерия (для фильтрации групп/номеров) |
| vins[..].criteriaURI | string | Да | Критерия (для фильтрации групп/номеров) |
| vins[..].title | string | - | Имя модели (из VIN справочника) |

#### **ВАЖНО!** ссылку формируем https://acat.online/api/catalogs/:type/:mark/:model/:modification?criteria=vins[..].criteriaURI
