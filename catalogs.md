# Типы и марки

## `GET /api/catalogs`

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
    		"image": "https://212709.selcdn.ru/autocatalog-online/main/marks/63.png",
			"SKD": false,
			"archival": false,
			"engine": false
    	  },
    	  {
			  "name": "Andoria",
              "value": "ANDORIA_ENGINE",
              "image": "https://212709.selcdn.ru/autocatalog-online/main/marks/162.png",
              "SKD": false,
              "archival": false,
              "engine": true
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
| name | string | - | Тип транспортного средства |
| value | string | Да | Сокращеное название типа транспортного средства |
| image | string | - | Путь до изображения |
| marks | array | - | Марки текущего типа |
| marks[..].name | string | - | Название марки |
| marks[..].value | string | - | Идентификатор марки |
| marks[..].image | string | - | Путь до изображения |
| marks[..].SDK | boolean | - | Параметр крупноузлового каталога |
| marks[..].archival | boolean | - | Параметр архивного каталога |
| marks[..].engine | boolean | - | Параметр каталога двигателей |


## `GET /:type/:mark[/:category]`

Для перехода к следующему уровню передайте в GET параметры value и marks[..].value.

### Пример запроса

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/CARS_NATIVE/AZLK
```

### ВАЖНО! При переходе на /api/catalogs/:type произоидет переадресация на /api/catalogs и будет получен тот же ответ 