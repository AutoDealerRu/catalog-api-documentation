Субаккаунты (followers) являются инструментом для контроля и распределения запросов к API между внутренними аккаунтами пользователя.  
Этот функционал подойдет таким пользователям, как разработчику интернет-магазинов, разработчику 1С конфигураций, тем кто поставляет наш каталог третим лицам.  
Чтобы этот функционал заработал, необходимо связаться по почте support@autodealer.ru с просьбой подключения партнерской программы.  
Если вы уже являетесь партнером, то схема работы проста:
- Для регистрации нового субаккаунта необходимо отправить [POST запрос](#Добавить-follower) с указанием вашего внутренного id субаккаунта и id [тарифа](https://github.com/Nazgard/catalog-api-documentation/blob/master/rates.md).
  Обратите внимание: субаккаунт должен быть уникален по id. При попытке создать 2 и более субаккаунта с одинаковым id приведут к ошибке.
- При запросах к API каталога в Header запроса нужно указать Follower: id партнера (как в вашей система учета)
- Если необходимо сменить тариф или id субаккаунта - предусмотрены методы [редактирования](#Редактировать-follower) и [удаления](#Удалить-follower)


**Список followers**
----
  Возвращает список followers.

* **URL**

  https://acat.online/api/dashboard/followers

* **Метод:**

  `GET`

* **Пример ответа:**
  ```json
    [
        {
            "id": "1",
            "rate": "5860f94350f75c86fe48992c",
            "limit_hits_hour": 1000,
            "limit_hits_day": 10000,
            "limit_hits_month": 200000,
            "limit_views_hour": 100,
            "limit_views_day": 2000,
            "limit_views_month": 10000
        }
    ]
  ```

* **Пример запроса:**

  ```bash
  curl -H 'Authorization: <token>' \
  -X GET https://acat.online/api/public/followers
  ```






**Информация о follower**
----
  Получить детальную информацию по follower (лимиты, статистика).

* **URL**

  https://acat.online/api/dashboard/followers/1

* **Метод:**

  `GET`

* **Пример ответа:**
  ```json
    {
        "id": "1",
        "rate": "5860f94350f75c86fe48992c",
        "limit_hits_hour": 1000,
        "limit_hits_day": 10000,
        "limit_hits_month": 200000,
        "limit_views_hour": 100,
        "limit_views_day": 2000,
        "limit_views_month": 10000,
        "consume": {
            "hit": {
                "hour": 0,
                "day": 5,
                "month": 5,
                "all": 5
            },
            "view": {
                "hour": 1,
                "day": 2,
                "month": 10,
                "all": 10
            }
        }
    }
  ```

* **Пример запроса:**

  ```bash
  curl -H 'Authorization: <token>' \
  -X GET https://acat.online/api/public/followers/1
  ```





**Добавить follower**
----
  Добавить нового follower.

* **URL**

  https://acat.online/api/dashboard/followers

* **Метод:**

  `POST`

* **Пример запроса:**
  ```json
    {
        "id": "2",
        "rate": "5860f94350f75c86fe48992c"
    }
  ```

* **Пример ответа:**
  ```json
    {
        "id": "2",
        "rate": "5860f94350f75c86fe48992c",
        "limit_hits_hour": 1000,
        "limit_hits_day": 10000,
        "limit_hits_month": 200000,
        "limit_views_hour": 100,
        "limit_views_day": 2000,
        "limit_views_month": 10000
    }
  ```

* **Пример запроса:**

  ```bash
  curl -H 'Authorization: <token>' \
  -H "Content-Type: application/json" -X POST -d '{"id":"2","rate":"5860f94350f75c86fe48992c"}' https://acat.online/api/public/followers
  ```




**Редактировать follower**
----
  Редактировать существующего follower.

* **URL**

  https://acat.online/api/dashboard/followers/2

* **Метод:**

  `PUT`

* **Пример запроса:**
  ```json
    {
        "id": "2",
        "rate": "5860f9dd50f75c86fe48992d"
    }
  ```

* **Пример ответа:**
  ```json
    {
        "id": "2",
        "rate": "5860f9dd50f75c86fe48992d",
        "limit_hits_hour": 1000,
        "limit_hits_day": 10000,
        "limit_hits_month": 200000,
        "limit_views_hour": 100,
        "limit_views_day": 2000,
        "limit_views_month": 10000
    }
  ```

* **Пример запроса:**

  ```bash
  curl -H 'Authorization: <token>' \
  -H "Content-Type: application/json" -X POST -d '{"id":"2","rate":"5860f9dd50f75c86fe48992d"}' https://acat.online/api/public/followers
  ```




**Удалить follower**
----
  Удалить существующего follower.

* **URL**

  https://acat.online/api/dashboard/followers/2

* **Метод:**

  `DELETE`

* **Пример запроса:**

  ```bash
  curl -H 'Authorization: <token>' \
  -X DELETE https://acat.online/api/public/followers/2
  ```
