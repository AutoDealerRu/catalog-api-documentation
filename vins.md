# Глобальный поиск по VIN

Результаты для каждого из каталогов немного отличаются,
но в каждом результате есть тип транспортного средства и марка.
На основе типа и марки можно парсить ответы в соответсвии со структурой.

### Пример запроса

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/search?vin=U5YFF24227L020768
```

### Пример ответа KIA, Hyundai

```json
{
    "vins": [
        {
            "vin": "U5YFF24227L020768",
            "mark": "KIA",
            "type": "CARS_FOREIGN",
            "country_short": "EUR",
            "family": "CEED",
            "model": "SEURPED06",
            "modification": "BSS6D2615",
            "model_name": "CEED 06 (2006-)"
        }
    ]
}
```

### Пример ответа Nissan, Infiniti

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
        }
    ]
}
```

### Пример ответа Toyota, Lexus

```json
{
    "type": "CARS_FOREIGN",
    "mark": "TOYOTA",
    "country_short_name": "US",
    "catalog_code": "522410",
    "model_code": "MCU25L-BWPNKA",
    "sysopt": "sysopt",
    "vin": "JTEHF21A**0076044",
    "complectation_code": "004"
}
```

### Пример ответа Abarth, Alfa Romeo, Fiat, Lancia

```json
[
    {
        "vin": "323B3118594",
        "type": "CARS_FOREIGN",
        "mark_short_name": "FIAT",
        "model_short_name": "LIN",
        "modification_short_name": "3M",
        "modification_name": "LINEA (2007-....)"
    }
]
```