# Избранное

## Матчи 
Список избранных матчей пользователя

### Список [GET /favorite/games]
+ Arguments
    + id: 11 (number) - ID матча.
    + dtime: 2016.02.05 20:00:00 (DateTime) - время проведения матча в формате YY.mm.dd H:m:s (? timezone UTC).
    + status: wait (string) - wait, live, cancel, fin
    + info:
        + score: 3-2 (string) - счет матча
        + part: 2 (number) - тайм
        + minute: 86 (number) - минута матча
    + home: (Team) - первая команда
        + id: 22 (number) - ID команды.
        + name: Барселона (string) - название команды на русском.
        + logo: //img.neverbet.com/barcelona.png (string) -  ссылка на лого команды.
        + country: ES (string len=2) - IATA код страны команды.
        + cards - карточки
            + yellow: 2 (number) - желтые карты
            + red: 0 (number) - красные карты
        + corners: 2  (number) - угловые
    + guest: (Team) - вторая команда
        + id: 21 (number) - ID команды.
        + name: Рома (string) - название команды на русском.
        + logo: //img.neverbet.com/roma.png (string) -  ссылка на лого команды.
        + country: IT (string len=2) - IATA код страны команды.
        + cards - карточки
            + yellow: 2 (number) - желтые карты
            + red: 0 (number) - красные карты
        + corners: 2  (number) - угловые
+ Response 200 (application/json)

        [
            {
               "id": 11,
                "dtime": "2016.02.05 20:00:00",
                "status" : "live",
                "info":{
                    "score": "3-0",
                    "part": 2,
                    "minute": 86
                },
                "home":{
                "id": 22,
                    "name": "Барселона",
                    "country": "ES",
                    "cards":{
                        "yellow":2,
                            "red":0
                    },
                    "corners": 2
                },
                "guest": {
                    "id":21,
                    "name": "Рома",
                    "country": "ES",
                    "cards":{
                        "yellow":4,
                        "red":1
                    },
                    "corners": 12
                }
            }
        ]

### Добавить матч в избранное [POST /favorite/games]

+ Request

    + Body

            +id: 12 (required, number) - ID матча 

+ Response 202

### Удалить матч из избранного [DELETE /favorite/games]

+ Request

    + Body

            +id: 12 (required, number) - ID матча 

+ Response 204



## Турниры
Список избранных турниров пользователя

### Список [GET /favorite/turnirs]
+ Arguments
    + id: (number) - ID турнира.
    + name: (string) - название турнира на русском.
    + country: (string len=2) - IATA код страны
    + icon: (string) - адрес иконки турнира

+ Response 200 (application/json)

        [
            {
                "id" : 12,
                "name": "Примьер-Лига",
                "country": "ES",
                "icon": "//img.neverbet.com/country/EN.png"
            }
        ]

### Добавить в избранное [POST /favorite/turnirs]

+ Request

    + Body

            +id: 12 (required, number) - ID матча 

+ Response 202

### Удалить  [DELETE /favorite/turnirs]

+ Request

    + Body

            +id: 12 (required, number) - ID матча 

+ Response 204


## Команды
Список избранных команд пользователя

### Список [GET /favorite/teams]
+ Arguments
    + id: (number) - ID команды.
    + name: (string) - название команды на русском.
    + country: (string len=2) - IATA код страны
    + icon: (string) - адрес иконки команды

+ Response 200 (application/json)

        [
            {
                "id" : 12,
                "name": "Барселона",
                "country": "ES",
                "icon": "//img.neverbet.com/team/barcelona.png"
            }
        ]

### Добавить в избранное [POST /favorite/teams]

+ Request

    + Body

            +id: 12 (required, number) - ID матча 

+ Response 202

### Удалить  [DELETE /favorite/teams]

+ Request

    + Body

            +id: 12 (required, number) - ID матча 

+ Response 204

## Закладки
Список избранных пользователем публикаций

### Список [GET /favorite/feeds{?offset}]
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
### Добавить в избранное [POST /favorite/feeds]

+ Request

    + Body

            +id: 12 (required, number) - ID матча 

+ Response 202

### Удалить  [DELETE /favorite/feeds]

+ Request

    + Body

            +id: 12 (required, number) - ID матча 

+ Response 204
