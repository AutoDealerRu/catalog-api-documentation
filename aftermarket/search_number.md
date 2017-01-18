# Поиск по номеру (search_number)

- Виды поисков:
  - поиск по неоригинальным номерам (номера каталога)
  - поиск по оригинальным номерам (кроссам)
  
## Пример запроса для поиска по неоригинальным номеру

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/CARS_FOREIGN/AFTERMARKET/search?number=C2G001ABE
```

### `GET /:type/AFTERMARKET/search?number=:number`
  
## Пример запроса для поиска по оригинальному номеру

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/CARS_FOREIGN/AFTERMARKET/search?original_number=1111281
```

### `GET /:type/AFTERMARKET/search?original_number=:number`

## ВАЖНО!
### 1. Указание типа (CARS_FOREIGN или TRUCKS_FOREIGN) не влияет на результат, отдаются все найденные запчасти всех типов
### 2. Ответ одинаковый для обоих видов запроса
### 3. Не указывать одновременно оба типа, в ответ придет ошибка
### 4. Искомый номер перед поиском очищаются от спецсимволов, пробелов. 
  
## Пример ответа

```json
{
    "numbers": [
    	{
            "type": "CARS_FOREIGN",
            "mark": "AFTERMARKET",
            "mark_short_name": "AC",
            "model_id": 4211,
            "modification_id": 12428,
            "group_id": 10130,
            "provider_id": 11005,
            "number": "C2G001ABE",
            "article_id": 116495492,
            "name": "AC ACE 4.6",
            "from_date": "1998-10-01T00:00:00.000Z",
            "to_date": null,
            "power_kW": 240,
            "power_hp": 326,
            "cubic_centimeters": 4601,
            "construction_type": "кабрио",
            "technical_information": {
                "chassis_configuration": null,
                "tonnage": "0.00",
                "engine_capacity": "4.600",
                "cylinder": "8",
                "voltage": null,
                "abs": null,
                "asr": null,
                "engine_type": "Бензиновый двигатель",
                "brake_type": null,
                "brake_system": "гидравлический",
                "fuel": "бензин",
                "catalyst_type": "с регулируемым катализатором (3-х ступенчатый)",
                "transmission": null,
                "refueling": "Впрыскивание во впускной коллектор/Карбюратор",
                "valves_per_combustion_chamber": "4"
            }
        },
        ...
    ],   
    "breadcrumbs": [
        {
            "name": "Каталог",
            "url": "/catalogs"
        },
        {
            "name": "Поиск",
            "url": "search"
        }
    ]
}
```

### Значения numbers

| Имя точка | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| type | string | Да | Тип кузова |
| mark | string | Да | Название каталога (всегда будет AFTERMARKET) |
| mark_short_name | string | Да | Сокращенное название марки |
| model_id | integer | Да | Идентифкационный номер модели |
| modification_id | integer | Да | Идентифкационный номер модификации |
| group_id | integer | Да | Идентифкационный номер группы |
| provider_id | integer | Да | ID производителя |
| number | string | Да | Номер |
| article_id | integer | Да | ID артикула |
| name | string | - | Название |
| from_date | null/date | - | Дата начала производства |
| to_date | null/date | - | Дата окончания производства |
| power_kW | integer | - | Мощность кВт |
| power_hp | integer | - | Лошадиных сил |
| cubic_centimeters | integer | - | Объем в куб. см. |
| construction_type | string | - | Тип конструкции |
| technical_information | object | - | Техническая информаци |
| technical_information.chassis_configuration | null / string | - | Конфигурация шасси |
| technical_information.tonnage | string | - | Тоннаж |
| technical_information.engine_capacity | string | - | Мощность двигателя |
| technical_information.cylinder | string | - | Количество цилиндров |
| technical_information.voltage | null / string | - | Вольтаж |
| technical_information.abs | null / string | - | АБС (антиблокировочная тормозная система) |
| technical_information.asr | null / string | - | АСР (регулировка привода ведущих колес) |
| technical_information.engine_type | null / string | - | Тип двигателя |
| technical_information.brake_type | null / string | - | Тип тормозов |
| technical_information.brake_system | null / string | - | Конфигурация тормозной системы |
| technical_information.fuel | null / string | - | Топливо |
| technical_information.catalyst_type | null / string | - | Тип катализатора |
| technical_information.transmission | null / string | - | Трансмиссия |
| technical_information.refueling | null / string | - | Перезаправка |
| technical_information.valves_per_combustion_chamber | null / string | - | Количество клапанов на камерусгорания |

### Значения breadcrumbs

| Имя точка | Тип | Описание |
| :---- | :------: | :--------------- |
| name | string | Имя хлебной крошки |
| url | string | Адрес текущей хлебной крошки |

## Пример запроса для перехода к описанию

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/CARS_FOREIGN/AFTERMARKET/AC/4211/12428/10130/11005/C2G001ABE/116495492
```

### `GET /:type/:mark/:mark_short_name/:model_id/:modification_id/:group_id/:provider_id/:number/:article_id`