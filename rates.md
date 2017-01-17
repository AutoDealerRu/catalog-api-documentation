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
            "_id": "5860f8fe50f75c86fe48992b",
            "name": "Демо",
            "vendor_code": "DEMO",
            "limit_views_hour": 50,
            "limit_views_day": 100,
            "limit_views_month": 2000,
            "limit_hits_hour": 100,
            "limit_hits_day": 1000,
            "limit_hits_month": 10000,
            "available_catalogs": [
                {
                    "type": "FULL"
                }
            ]
        },
        {
            "_id": "5860f94350f75c86fe48992c",
            "name": "Тариф Легковой",
            "vendor_code": "LIGHT",
            "limit_hits_hour": 1000,
            "limit_hits_day": 10000,
            "limit_hits_month": 200000,
            "limit_views_hour": 100,
            "limit_views_day": 2000,
            "limit_views_month": 10000,
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
            ]
        },
        {
            "_id": "5860f9dd50f75c86fe48992d",
            "name": "Тариф Грузовой",
            "vendor_code": "HEAVY",
            "limit_hits_hour": 1000,
            "limit_hits_day": 10000,
            "limit_hits_month": 200000,
            "limit_views_hour": 100,
            "limit_views_day": 2000,
            "limit_views_month": 10000,
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
                }
            ]
        },
        {
            "_id": "5860fa4650f75c86fe48992e",
            "name": "Весь каталог",
            "vendor_code": "ALL",
            "limit_hits_hour": 1000,
            "limit_hits_day": 10000,
            "limit_hits_month": 200000,
            "limit_views_hour": 100,
            "limit_views_day": 2000,
            "limit_views_month": 10000,
            "available_catalogs": [
                {
                    "type": "FULL"
                }
            ]
        }
    ]
  ```

* **Пример запроса:**

  ```bash
  curl -X GET https://acat.online/api/public/rates
  ```