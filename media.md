# Медиа
Описание методов раздела Медиа в API [Prosports](README.md)

## Фото

### Фотоальбомы [GET /photos/{?offset}]
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
                "thumb":"//img.prosports.kz/user/u56.jpg"
                "dtime": "2016.01.05 20:30",
                "count":12
            }
        ]
        
### Фото в  альбоме [GET /photos/album/{id}]
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
                "thumb":"//img.prosports.kz/user/u56.jpg"
                "src": "//img.prosports.kz/user/u56_big.jpg"
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
                "thumb":"//img.prosports.kz/videos/u56.jpg"
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
                "thumb":"//img.prosports.kz/videos/u56.jpg"
                "src": "//img.prosports.kz/videos/u56.mp4"
            }
        ]
