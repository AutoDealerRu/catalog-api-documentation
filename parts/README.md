# ТИПЫ И МАРКИ

## `GET /api/public/types`

Получение перечня типов и марок, возвращает объект с десятью каталогами (fiat, ... & parts)

### Пример запроса

```bash
curl -X GET https://acat.online/api/public/types
```
### Пример ответа

```json
{
  ...,
  "parts": {
      "types": [
          "CARS_FOREIGN",
          "TRUCKS_FOREIGN",
          "BUS",
          "ENGINE",
          "MOTORCYCLE",
          "SPECIAL_TECH_FOREIGN"
      ],
      "marks": [
          "mitsubishi",
          "ford",
          "opel",
          "mazda",
          "subaru",
          "vauxhall",
          "peugeot",
          "citroen",
          "volvo",
          "honda",
          "suzuki",
          "isuzu",
          "chrysler",
          "dodge",
          "jeep",
          "plymouth",
          "chevrolet",
          "jaguar",
          "land-rover",
          "porsche",
          "chery",
          "volvo-trucks",
          "man",
          "renault",
          "dacia",
          "ssangyong",
          "lexus",
          "toyota",
          "audi",
          "seat",
          "skoda",
          "vw",
          "bmw",
          "bmw-moto",
          "mini",
          "rolls-royce",
          "smart",
          "infiniti",
          "nissan",
          "mercedes",
          "kia",
          "hyundai",
          "saab",
          "daf",
          "iveco"
      ]
  }
}
```
