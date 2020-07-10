# ТИПЫ И МАРКИ

## `GET /api/public/types`

Получение перечня типов и марок, возвращает объект с десятью каталогами (fiat, bmw, nissan, kia, toyota, etka, a2d, renault, ssangyong, mercedes) и объектом mark

### Пример запроса

```bash
curl -X GET https://acat.online/api/public/types
```
### Пример ответа

```json
{
    ...,
    "fiat": {
        "types": [
            "CARS_FOREIGN"
        ],
        "marks": [
            "FIAT",
            "LANCIA",
            "ALFA_ROMEO",
            "ABARTH"
        ]
    },...
}
```
