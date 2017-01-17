# Модификации (modifications)

## `GET /:type/:mark/:mark_short_name/:model_id`

Возвращает объект с двумя массивам modifications и breadcrumbs

| Конечная точка | Описание |
| :---- | :--------------- |
| GET /CARS_FOREIGN/AFTERMARKET/AC/4211 | Модификации AC ACE |

### Пример запроса

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/CARS_FOREIGN/AFTERMARKET/AC/4211
```

### Пример ответа

```json
{
    "modifications": [
        {
            "type": "CARS_FOREIGN",
            "mark": "AFTERMARKET",
            "mark_short_name": "AC",
            "model_id": 4211,
            "modification_id": 12428
            "model_name_eng": "ACE",
            "name": "AC ACE",
            "modification_type": "4.6",
            "from_date": "1998-10-01T00:00:00.000Z",
            "to_date": null,
            "power_kW": 240,
            "power_hp": 326,
            "cubic_centimeters": 4601,
            "construction_type": "кабрио",
            "construction_description": {
                "drive_type": "Привод на задние колеса",
                "doors": 0,
                "tank": 0
            },
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
            },
        },
        ...
    ],
    "breadcrumbs": [
        ...
        ,{
            "name": "ACE",
            "url": "4211"
        }
    ]
}
```

### Значения countries

| Имя точка | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| type | string | - | Тип кузова |
| mark | string | - | Название каталога (всегда будет AFTERMARKET) |
| mark_short_name | string | - | Сокращенное название марки |
| model_id | integer | - | Идентифкационный номер модели |
| model_name_eng | string | - | Название модели на английском |
| modification_id | integer | Да | Идентифкационный номер модификации |
| name | string | - | Название модификации |
| modification_type | string | - | Тип модификации |
| from_date | null/date | - | Дата начала производства |
| to_date | null/date | - | Дата окончания производства |
| power_kW | integer | - | Мощность кВт |
| power_hp | integer | - | Лошадиных сил |
| cubic_centimeters | integer | - | Объем в куб. см. |
| construction_type | string | - | Тип конструкции |
| construction_description | object | - | Описание конструкции |
| construction_description.drive_type | string | - | Тип привода |
| construction_description.doors | integer | - | Количество дверей (актуально для грузовых) |
| construction_description.tank | integer | - | Бак |
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


## `GET /:type//:mark/:mark_short_name/:model_id/:modification_id`

Для перехода к списку групп нужно выбрать модифацию и передать ее идентификатор (modification_id) в GET параметры