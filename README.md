# Типы и марки

## `GET /:type/:mark`

Возвращает массив

| Конечная точка | Описание |
| :---- | :--------------- |
| GET /api/catalogs | Список типов машин и их марок |

### Пример запроса

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs
```

### Пример ответа

```json
[
    {
    	"index": 1,
    	"name": "Легковые (отечественные)",
    	"value": "CARS_NATIVE",
    	"image": "http://212709.selcdn.ru/autocatalog-online/main/types/1.png",
    	"marks": [
    	  {
    		"name": "АЗЛК",
    		"value": "AZLK",
    		"image": "63"
    	  },
    	  {
    		"name": "ВАЗ",
    		"value": "VAZ",
    		"image": "40"
    	  },
    	  ...
        ]
    },
    ...
]
```

### Значения

| Имя точка | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| index | integer | - | Порядковый номер |
| name | string | - | Название типа |
| value | string | Да | Сокращеное название типа |
| image | string | - | Путь до изображения типа |
| marks | array of objects | - | Марки текущего типа |

### Значения marks

| Имя точка | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| name | string | - | Название марки |
| value | string | Да | Сокращеное название типа |
| image | string | - | Путь до изображения марки |


## `GET /:type/:mark`

Для перехода к следующему уровню передайте в GET параметры value и marks[0].value

### Пример запроса

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/CARS_NATIVE/AZLK
```

### ВАЖНО! При переходе на /api/catalogs/:type произоидет переадресация на /api/catalogs и будет получен тот же ответ 