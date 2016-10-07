# Медиа
Описание методов раздела Медиа в API [Kairat](README.md)

## Фото

### Фотоальбомы [GET /photos/{?offset}]
Возвращает список фотоальбомов

+ Arguments
    + id: (number) - ID номер альбома 
    + name: (string) - название альбома
    + thumb: (string) - адрес к обложке альбома
    + dtime: (DateTime) - дата и время публикации в формате Y.m.d H:m 
    + count: (number) - кол-во фото в альбоме
        
+ Parameters
    + offset: 12 (number) - отступ для выборки

+ Response 200 (application/json)

        [
            {
                "id": 1235,
                "name":"Все голы в сезоне",
                "thumb":"//img.kairat.kz/user/u56.jpg",
                "dtime": "2016.01.05 20:30",
                "count":12
            },
            {
                "id": 1236,
                "name":"Все голы в сезоне",
                "thumb":"//img.kairat.kz/user/u56.jpg",
                "dtime": "2016.01.05 20:30",
                "count":12
            }
        ]
        
### Фото в альбоме [GET /photos/album/{id}]
Возвращает список фото в альбоме

+ Arguments
    + id: (number) - ID фото 
    + thumb: (string) - адрес к миниатюре
    + src: (string) - адрес к большой фотке
        
+ Parameters
    + id: (required, number) - ID публикации 

+ Response 200 (application/json)

        [
            {
                "id": 1235,
                "thumb":"//img.kairat.kz/photos/ZU7ksJU-zKE.jpg",
                "src": "//img.kairat.kz/photos/ZU7ksJU-zKE_big.jpg"
            },
            {
                "id": 1233,
                "thumb":"//img.kairat.kz/photos/Гейнрих.jpg",
                "src": "//img.kairat.kz/photos/Гейнрих_big.jpg"
            }
        ]
        
## Видео

### Видео альбомы [GET /videos/{?offset}]
+ Arguments
    + id: (number) - ID номер альбома 
    + name: (string) - название альбома
    + thumb: (string) - адрес к обложке альбома
    + dtime: (DateTime) - дата и время публикации в формате Y.m.d H:m 
    + count: (number) - кол-во фото в альбоме
        
+ Parameters
    + offset: 12 (number) - отступ для выборки

+ Response 200 (application/json)

        [
            {
                "id": 1235,
                "name":"Все голы в сезоне",
                "thumb":"//img.kairat.kz/videos/u56.jpg",
                "dtime": "2016.01.05 20:30",
                "count":12
            }
        ]
        
### Видео в альбоме [GET /videos/album/{id}]
+ Arguments
    + id: (number) - ID фото 
    + thumb: (string) - адрес к миниатюре
    + src: (string) - адрес к видео
        
+ Parameters
    + id: (required, number) - ID публикации 

+ Response 200 (application/json)

        [
            {
                "id": 1235,
                "thumb":"//img.kairat.kz/videos/u56.jpg",
                "src": "//img.kairat.kz/videos/u56.mp4"
            }
        ]
