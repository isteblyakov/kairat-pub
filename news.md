# Новости
Описание методов раздела Новости в API [Prosports](README.md)

## Новости
Список главных новостей

### Публикации [GET /feeds/{?offset}]
+ Arguments
    + id: 12 (number) - ID номер публикации 
    + author: (Author) - автор публикации
        + type: owner (string) - тип авторства: owner - владелец, repost - перепубликации
        + id: 12 (number) - ID автора
        + rate: 33 (number) - рейтинг авторa
        + name: Костян Филатов (string) - имя автора
        + thumb: "//img.neverbet.com/thumb/u56.jpg" (string) - адрес к аватарке пользователя
    + dtime: 2016.01.05 20:30 (DateTime) - дата и время публикации в формате Y.m.d H:m 
    + comments: 12 (number) - кол-во комментариев к публикации
    + rate: 3 (number) - рейтинг публикации
    + body: (string) - сообщение
    + tags: (Array) - массив тегов к публикации
        
+ Parameters
    + offset: 12 (number) - отступ для выборки

+ Response 200 (application/json)

        [
            {
                "id": 1235,
                "author":{
                    "type":"owner",
                    "id":56,
                    "rate":33,
                    "name":"Костян Филатов",
                    "thumb":"//img.neverbet.com/user/u56.jpg"
                },
                "dtime": "2016.01.05 20:30",
                "comments":12,
                "rate":3,
                "body":"<img src='//img.neverbet.com/feeds/u56sdf23gf.jpg'/>Русский форвард #Вашингтона оформил 14-й хет-трик за карьеру в НХЛ",
                "tags": [
                    "Вашингтон"
                ]
            }
        ]

## Популярные новости
Список популярных новостей

### Публикации [GET /feeds/pop/{?offset}]
+ Arguments
    + id: 12 (number) - ID номер публикации 
    + author: (Author) - автор публикации
        + type: owner (string) - тип авторства: owner - владелец, repost - перепубликации
        + id: 12 (number) - ID автора
        + rate: 33 (number) - рейтинг авторa
        + name: Костян Филатов (string) - имя автора
        + thumb: "//img.neverbet.com/thumb/u56.jpg" (string) - адрес к аватарке пользователя
    + dtime: 2016.01.05 20:30 (DateTime) - дата и время публикации в формате Y.m.d H:m 
    + comments: 12 (number) - кол-во комментариев к публикации
    + rate: 3 (number) - рейтинг публикации
    + body: (string) - сообщение
    + tags: (Array) - массив тегов к публикации
        
+ Parameters
    + offset: 12 (number) - отступ для выборки

+ Response 200 (application/json)

        [
            {
                "id": 1235,
                "author":{
                    "type":"owner",
                    "id":56,
                    "rate":33,
                    "name":"Костян Филатов",
                    "thumb":"//img.neverbet.com/user/u56.jpg"
                },
                "dtime": "2016.01.05 20:30",
                "comments":12,
                "rate":3,
                "body":"<img src='//img.neverbet.com/feeds/u56sdf23gf.jpg'/>Русский форвард #Вашингтона оформил 14-й хет-трик за карьеру в НХЛ",
                "tags": [
                    "Вашингтон"
                ]
            }
        ]
  
## Публикация
Подробное описание Публикации

### Подбробнее о публикации [GET /feed/{id}]
+ Arguments
    + id: 12 (number) - ID номер публикации 
    + author: (Author) - автор публикации
        + type: owner (string) - тип авторства: owner - владелец, repost - перепубликации
        + id: 12 (number) - ID автора
        + rate: 33 (number) - рейтинг авторa
        + name: Костян Филатов (string) - имя автора
        + thumb: "//img.neverbet.com/thumb/u56.jpg" (string) - адрес к аватарке пользователя
    + dtime: 2016.01.05 20:30 (DateTime) - дата и время публикации в формате Y.m.d H:m 
    + comments: 12 (number) - кол-во комментариев к публикации
        + id: 12 (number) - ID комментария
        + author: (Author) - автор публикации
            + id: 12 (number) - ID автора
            + rate: 33 (number) - рейтинг авторa
            + name: Костян Филатов (string) - имя автора
            + thumb: "//img.neverbet.com/thumb/u56.jpg" (string) - адрес к аватарке пользователя
        + dtime: 2016.01.05 20:30 (DateTime) - дата и время публикации в формате Y.m.d H:m 
        + body: (string) - комментарий
    + rate: 3 (number) - рейтинг публикации
    + body: (string) - сообщение
    + tags: (Array) - массив тегов к публикации
        
+ Parameters
    + id: 12 (required, number) - ID публикации 

+ Response 200 (application/json)

        {
            "id": 1235,
            "author":{
                "type":"owner",
                "id":56,
                "rate":33,
                "name":"Костян Филатов",
                "thumb":"//img.neverbet.com/user/u56.jpg"
            },
            "dtime": "2016.01.05 20:30",
            "comments":[
                {
                    "id": 1235,
                    "author":{
                        "id":56,
                        "rate":33,
                        "name":"Костян Филатов",
                        "thumb":"//img.neverbet.com/user/u56.jpg"
                    },
                    "dtime": "2016.01.05 20:30",
                    "body":"Думаю сейчас ставить на Примеру...Есть идеи?"
                }
            ],
            "rate":3,
            "body":"<img src='//img.neverbet.com/feeds/u56sdf23gf.jpg'/>Русский форвард #Вашингтона оформил 14-й хет-трик за карьеру в НХЛ",
            "tags": [
                "Вашингтон"
            ]
        }

## Комментарии
Комментарии к Публикации

### Комментарии [GET /feed/{id}/comments]
+ Arguments
    + id: 12 (number) - ID номер публикации 
    + author: (Author) - автор публикации
        + id: 12 (number) - ID автора
        + rate: 33 (number) - рейтинг авторa
        + name: Костян Филатов (string) - имя автора
        + thumb: "//img.neverbet.com/thumb/u56.jpg" (string) - адрес к аватарке пользователя
    + dtime: 2016.01.05 20:30 (DateTime) - дата и время публикации в формате Y.m.d H:m 
    + body: (string) - сообщение
        
+ Parameters
    + id: 12 (required, number) - ID публикации 

+ Response 200 (application/json)

        [
                {
                    "id": 1235,
                    "author":{
                        "id":56,
                        "rate":33,
                        "name":"Костян Филатов",
                        "thumb":"//img.neverbet.com/user/u56.jpg"
                    },
                    "dtime": "2016.01.05 20:30",
                    "body":"Думаю сейчас ставить на Примеру...Есть идеи?"
                }
        ]

### Написать Комментарии [POST /feed/{id}/comments]

+ Parameters
    + id: 12 (required, number) - ID публикации 

+ Request (application/json)

    + Body

            {
                "body": "Думаю сейчас ставить на Примеру...Есть идеи?"
            }
    
+ Response 204

### Удалить Комментарии [DELETE /feed/{id}/comments]

+ Parameters
    + id: 12 (required, number) - ID комментария 

+ Response 204
