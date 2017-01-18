# Информация по номеру (number_information)

## `GET /:type/:mark/:mark_short_name/:model_id/:modification_id/:group_id/:provider_id/:number/:article_id`

Возвращает объект с объектом info и массивом объектов breadcrumbs

| Конечная точка | Описание |
| :---- | :--------------- |
| GET /CARS_FOREIGN/AFTERMARKET/AC/4211/12428/12096/11353/XLS011/129385604 | Информация AC ACE 4.6 Масла XLS011 (Масло осевого редуктора)|

### Пример запроса

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/CARS_FOREIGN/AFTERMARKET/AC/4211/12428/12096/11353/XLS011/129385604
```

### Пример ответа

```json
{
    "info": {
    	"number": "C2G001ABE",
    	"original_numbers": [
            "123456789"    	
    	]
    	"status": "Нормальный",
    	"name": "Комплект тормозных колодок, дисковый тормоз",
    	"packing_unit": 0,
    	"package_amount": 0,
    	"can_be_changed": false,
    	"independent_use": false,
    	"accessories": false,
    	"require_mandatory_designation": false,
    	"criteries": [
    	  {
    		"value": "задний мост",
    		"name": "Сторона установки"
    	  },
    	  ...
    	  {
    		"value": "54",
    		"name": "Высота [мм]"
    	  },
    	  ...
    	  {
    		"name": "До года выпуска",
    		"value": "Fri Oct 01 1999 06:00:00 GMT+0600 (+06)"
    	  }
    	],
    	"images": [
    	  {
    		"alt": "Фотография",
    		"image": "AFTERMARKET/details/38/2544107.jpg"
    	  }
    	],
    	"provider": {
    	  "id": 11005,
    	  "name": "ABE",
    	  "image": "AFTERMARKET/logos/11005"
    	},
    	"crosses": [
            {
                "brand": "FORD",
                "original_number": "1111281"
            },
            ...
        ]
    },   
    "breadcrumbs": [
        ...
        ,{            
            "name": "Масло осевого редуктора",
            "url": "11353/XLS011/129385604"
        }
    ]
}
```

### Значения info

| Имя точка | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| type | string | - | Тип кузова |
| number | string | Да | Номер |
| original_numbers | array of strings | - | Номера EAN (оригинальные) |
| status | string | - | Статус детали |
| name | string | - | Название детали |
| packing_unit | integer | - | Упаковачная единица |
| package_amount | integer | - | Количество в упаковке |
| can_be_changed | boolean | - | Сменная деталь |
| independent_use | boolean | - | Для самостоятельного применения |
| accessories | boolean | - | Принадлежности |
| require_mandatory_designation | boolean | - | Требует обязательного обозначения |
| criteries | array of objects | - | Критерии |
| criteries.name | string | - | Имя критерии |
| criteries.value | string / date | - | Значение критерии |
| images | array of objects | - | Изображения |
| images.image | string | - | Путь до изображения детали |
| images.alt | string / date | - | Название изображения |
| crosses | array of objects | - | Кроссы |
| crosses.brand | string | - | Бренд детали |
| crosses.original_number | string / date | - | Оригинальный номер детали |
| provider | object | - | Производитель |
| provider.id | integer | Да | ID производителя |
| provider.name | string | - | Название производителя |
| provider.image | string | - | Путь до изображения производителя |

Если имя критерии "До года выпуска" или "Начиная с года выпуска", то значение - дата, в остальных случаях строка

### Значения breadcrumbs

| Имя точка | Тип | Описание |
| :---- | :------: | :--------------- |
| name | string | Имя хлебной крошки |
| url | string | Адрес текущей хлебной крошки |

## Пример получения списка применяемости по номеру

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/CARS_FOREIGN/AFTERMARKET/search?number=C2G001ABE
```

### Пример ответа

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


### Пример запроса для перехода к описанию

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/CARS_FOREIGN/AFTERMARKET/AC/4211/12428/10130/11005/C2G001ABE/116495492
```
#### `GET /:type/:mark/:mark_short_name/:model_id/:modification_id/:group_id/:provider_id/:number/:article_id`