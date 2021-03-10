**Список тарифов**
----
  Возвращает список текущих тарифов.

* **URL**

  https://acat.online/api/public/rates

* **Метод:**

  `GET`

* **Пример ответа:**
  ```json
    [
    {
        "_id": "5860f94350f75c86fe48992c",
        "name": "Легковой",
        "vendor_code": "LIGHT",
        "available_catalogs": [
            {
                "type": "CATEGORY",
                "value": "CARS_NATIVE"
            },
            {
                "type": "CATEGORY",
                "value": "CARS_FOREIGN"
            },
            {
                "type": "CATEGORY",
                "value": "MOTORCYCLE"
            }
        ],
        "limit_hits_hour": 1000,
        "limit_hits_day": 2000,
        "limit_hits_month": 20000,
        "limit_views_hour": 1000,
        "limit_views_day": 2000,
        "limit_views_month": 20000,
        "level": 2,
        "fullName": "Легковой"
    },
    {
        "_id": "5def13508119300b24222174",
        "name": "API 250",
        "fullName": "Весь каталог API 250.000",
        "vendor_code": "API250",
        "available_catalogs": [
            {
                "type": "FULL"
            }
        ],
        "limit_hits_hour": 5000,
        "limit_hits_day": 10000,
        "limit_hits_month": 250000,
        "limit_views_hour": 5000,
        "limit_views_day": 10000,
        "limit_views_month": 250000,
        "level": 7
    },
    {
        "_id": "5def13508119300b24222175",
        "name": "API 1000",
        "fullName": "Весь каталог API 1.000.000",
        "vendor_code": "API1000",
        "available_catalogs": [
            {
                "type": "FULL"
            }
        ],
        "limit_hits_hour": 10000,
        "limit_hits_day": 50000,
        "limit_hits_month": 1000000,
        "limit_views_hour": 10000,
        "limit_views_day": 50000,
        "limit_views_month": 1000000,
        "level": 9
    },
    {
        "_id": "5860f8fe50f75c86fe48992b",
        "name": "Демо",
        "vendor_code": "DEMO",
        "available_catalogs": [
            {
                "type": "FULL"
            }
        ],
        "limit_views_hour": 300,
        "limit_views_day": 300,
        "limit_views_month": 300,
        "limit_hits_hour": 300,
        "limit_hits_day": 300,
        "limit_hits_month": 300,
        "level": 1,
        "fullName": "Демо"
    },
    {
        "_id": "5860f9dd50f75c86fe48992d",
        "name": "Грузовой",
        "vendor_code": "HEAVY",
        "available_catalogs": [
            {
                "type": "CATEGORY",
                "value": "TRUCKS_NATIVE"
            },
            {
                "type": "CATEGORY",
                "value": "TRUCKS_FOREIGN"
            },
            {
                "type": "CATEGORY",
                "value": "BUS"
            },
            {
                "type": "CATEGORY",
                "value": "ENGINE"
            }
        ],
        "limit_hits_hour": 1000,
        "limit_hits_day": 2000,
        "limit_hits_month": 20000,
        "limit_views_hour": 1000,
        "limit_views_day": 2000,
        "limit_views_month": 20000,
        "level": 3,
        "fullName": "Грузовой"
    },
    {
        "_id": "5860fa4650f75c86fe48992e",
        "name": "Весь каталог",
        "vendor_code": "ALL",
        "available_catalogs": [
            {
                "type": "FULL"
            }
        ],
        "limit_hits_hour": 1000,
        "limit_hits_day": 2000,
        "limit_hits_month": 20000,
        "limit_views_hour": 1000,
        "limit_views_day": 2000,
        "limit_views_month": 20000,
        "level": 4,
        "fullName": "Весь каталог"
    },
    {
        "_id": "58da50bc6d3ec0611d5527f2",
        "name": "Нулевой",
        "vendor_code": "ZERO",
        "available_catalogs": [],
        "limit_views_hour": 0,
        "limit_views_day": 0,
        "limit_views_month": 0,
        "limit_hits_hour": 0,
        "limit_hits_day": 0,
        "limit_hits_month": 0,
        "level": 0,
        "fullName": "Нулевой"
    },
    {
        "_id": "5def13508119300b24222171",
        "name": "Весь каталог 100",
        "fullName": "Весь каталог 100.000",
        "vendor_code": "ALL100",
        "available_catalogs": [
            {
                "type": "FULL"
            }
        ],
        "limit_hits_hour": 5000,
        "limit_hits_day": 10000,
        "limit_hits_month": 100000,
        "limit_views_hour": 5000,
        "limit_views_day": 10000,
        "limit_views_month": 100000,
        "level": 6
    },
    {
        "_id": "5def13508119300b24222172",
        "name": "Весь каталог 1000",
        "fullName": "Весь каталог 1.000.000",
        "vendor_code": "ALL1000",
        "available_catalogs": [
            {
                "type": "FULL"
            }
        ],
        "limit_hits_hour": 10000,
        "limit_hits_day": 50000,
        "limit_hits_month": 1000000,
        "limit_views_hour": 10000,
        "limit_views_day": 50000,
        "limit_views_month": 1000000,
        "level": 8
    },
    {
        "_id": "5def13508119300b24222173",
        "name": "API 100",
        "fullName": "Весь каталог API 100.000",
        "vendor_code": "API100",
        "available_catalogs": [
            {
                "type": "FULL"
            }
        ],
        "limit_hits_hour": 5000,
        "limit_hits_day": 10000,
        "limit_hits_month": 100000,
        "limit_views_hour": 5000,
        "limit_views_day": 10000,
        "limit_views_month": 100000,
        "level": 5
    },
    {
        "_id": "5def13508119300b24222176",
        "name": "API 2000",
        "fullName": "Весь каталог API 2.000.000",
        "vendor_code": "API2000",
        "available_catalogs": [
            {
                "type": "FULL"
            }
        ],
        "limit_hits_hour": 10000,
        "limit_hits_day": 100000,
        "limit_hits_month": 2000000,
        "limit_views_hour": 10000,
        "limit_views_day": 100000,
        "limit_views_month": 2000000,
        "level": 10
    }
]
  ```

* **Пример запроса:**

  ```bash
  curl -X GET https://acat.online/api/public/rates
  ```
