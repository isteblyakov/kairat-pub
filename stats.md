# Статистика
Описание методов раздела Статиска API [Kairat](README.md)

## Список турниров
Возвращает список турниров по группам

### Список [GET /turnirs]
+ Arguments
    + name: (string) - название группы.
    + groups: (Array) - список подгрупп
    + icon: (string) - адрес иконки группы
    + turnirs: (Array) - список турниров в группе/подгруппе
        + id: (number) - ID турнира.
        + name: (string) - название турнира на русском.
        + icon: (string) - адрес иконки турнира

+ Response 200 (application/json)

        [
            {
                "name": "Популярные",
                "turnirs":[
                    {
                        "id" : 12,
                        "name": "Примьер-Лига",
                        "icon": "//img.kairat.kz/country/EN.png"
                    }
                ]
            },
            {
                "name": "Национальные",
                "groups":[
                    {
                        "name": "Англия",
                        "icon": "//img.kairat.kz/country/EN.png",
                        "turnirs":[
                            {
                                "id" : 12,
                                "name": "Примьер-Лига",
                                "icon": "//img.kairat.kz/country/EN.png",
                            },
                            {
                                "id" : 13,
                                "name": "Чемпионшип",
                                "icon": "//img.kairat.kz/country/EN.png",
                            }
                        ]
                    }
                ]
            }
        ]
        
## Турнир
Подробное описание туринира

### Описание туринира [GET /turnir/{turnir_id}]
+ Arguments
    + id: (number) - ID турнира
    + name: (string) - название турнира на русском.
    + descr: (string) - описание турнира
    + country: (string len=2) - IATA код страны турнира 
    + logo: (string) - ссылка на лого турнира.
    + feeds: (Array) - последние новости/публикации по турниру
        + id: 12 (number) - ID номер публикации 
        + author: (Author) - автор публикации
            + type: owner (string) - тип авторства: owner - владелец, repost - перепубликации
            + id: 12 (number) - ID автора
            + rate: 33 (number) - рейтинг авторa
            + name: Костян Филатов (string) - имя автора
            + thumb: "//img.kairat.kz/thumb/u56.jpg" (string) - адрес к аватарке пользователя
        + dtime: 2016.01.05 20:30 (DateTime) - дата и время публикации в формате Y.m.d H:m 
        + comments: 12 (number) - кол-во комментариев к публикации
        + rate: 3 (number) - рейтинг публикации
        + body: (string) - сообщение
        + tags: (Array) - массив тегов к публикации
        
+ Parameters
    + turnir_id: 12 (required, number) - ID туринира 

+ Response 200 (application/json)

        {
                "id" : 12,
                "name": "Премьер-Лига",
                "descr": "Чемпионат Англии по футболу",
                "country": "EN",
                "logo": "//img.kairat.kz/turnir/enpremier.png",
                "feeds":[
                    {
                        "id": 1235,
                        "author":{
                            "type":"owner",
                            "id":56,
                            "rate":33,
                            "name":"Костян Филатов",
                            "thumb":"//img.kairat.kz/user/u56.jpg"
                        },
                        "dtime": "2016.01.05 20:30",
                        "comments":12,
                        "rate":3,
                        "body":"<img src='//img.kairat.kz/feeds/u56sdf23gf.jpg'/>Русский форвард #Вашингтона оформил 14-й хет-трик за карьеру в НХЛ",
                        "tags": [
                            "Вашингтон"
                        ]
                    }
                ]
        }   
        
## Новости
Новости/публикации по турниру

### Новости турнира [GET /turnir/{turnir_id}/feeds/{?offset}]
+ Arguments
    + id: 12 (number) - ID номер публикации 
    + author: (Author) - автор публикации
        + type: owner (string) - тип авторства: owner - владелец, repost - перепубликации
        + id: 12 (number) - ID автора
        + rate: 33 (number) - рейтинг авторa
        + name: Костян Филатов (string) - имя автора
        + thumb: "//img.kairat.kz/thumb/u56.jpg" (string) - адрес к аватарке пользователя
    + dtime: 2016.01.05 20:30 (DateTime) - дата и время публикации в формате Y.m.d H:m 
    + comments: 12 (number) - кол-во комментариев к публикации
    + rate: 3 (number) - рейтинг публикации
    + body: (string) - сообщение
    + tags: (Array) - массив тегов к публикации
    
+ Parameters
    + turnir_id: 12 (required, number) - ID турнира
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
                    "thumb":"//img.kairat.kz/user/u56.jpg"
                },
                "dtime": "2016.01.05 20:30",
                "comments":12,
                "rate":3,
                "body":"<img src='//img.kairat.com/feeds/u56sdf23gf.jpg'/>Русский форвард #Вашингтона оформил 14-й хет-трик за карьеру в НХЛ",
                "tags": [
                    "Вашингтон"
                ]
            }  
        ]
        
## Таблица
Турнирная таблица. Если не задан сезон, таблицу на данный сезон

### Турнирная таблица [GET /turnir/{turnir_id}/table/{?season}]
+ Arguments
    + seasons: (Object) - список доступных сезонов
        + value: name - номер сезона / название сезона
    + season: (string) - название сезона
    + table: (Object)
        + name : (Array) - название таблицы
            + (Array[10]) - [id команды, код страны, название команды, всего игр, выйграно, ничьи, проиграно, голов забито, голов пропущенно, очков]
        

+ Parameters
    + turnir_id: 12 (required, number) - ID команды integer
    + season: 2016 (string) - сезон для выборки, передается год окончание сезона

+ Response 200 (application/json)

        {
               "seasons":{
                    "2012":"2011/2012",
                    "2015":"2014/2015",
                    "2016":"2015/2016",
                },
               "season":"2015/2016",
               "table":{
                    "Основная таблица":[
                        [223,"ES","Вестерн Сити",16,9,3,4,16,9,30],
                        [125,"ES","Леванте",16,9,3,4,16,9,28],
                        [34,"ES","Арсенал",16,9,3,4,16,9,27],
                        [567,"ES","Вестерн Сити",16,9,3,4,16,9,20],
                        [12,"ES","Арсенал",16,9,3,4,16,9,19],
                        [67,"ES","Леванте Сити",16,9,3,4,16,9,6]
                    ],
                    "Последние 5 туров":[
                        [223,"ES","Вестерн Сити",16,9,3,4,16,9,30],
                        [125,"ES","Леванте",16,9,3,4,16,9,28],
                        [34,"ES","Арсенал",16,9,3,4,16,9,27],
                        [567,"ES","Вестерн Сити",16,9,3,4,16,9,20],
                        [12,"ES","Арсенал",16,9,3,4,16,9,19],
                        [67,"ES","Леванте Сити",16,9,3,4,16,9,6]
                    ]
                }
        }
        
## Матчи
Матчи в турнире

### Матчи [GET /turnir/{turnir_id}/games/{?season}{?tour_id}]
+ Arguments
    + tours: (Object)  - список доступных турниров
        + value: name - номер тура / название тура
    + seasons: (Object) - список доступных сезонов
        + value: name - номер сезона / название сезона
    + games: (Array) - список игр
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
            + logo: //img.kairat.com/barcelona.png (string) -  ссылка на лого команды.
            + country: ES (string len=2) - IATA код страны команды.
            + cards - карточки
                + yellow: 2 (number) - желтые карты
                + red: 0 (number) - красные карты
            + corners: 2  (number) - угловые
        + guest: (Team) - вторая команда
            + id: 21 (number) - ID команды.
            + name: Рома (string) - название команды на русском.
            + logo: //img.kairat.com/roma.png (string) -  ссылка на лого команды.
            + country: IT (string len=2) - IATA код страны команды.
            + cards - карточки
                + yellow: 2 (number) - желтые карты
                + red: 0 (number) - красные карты
            + corners: 2  (number) - угловые

+ Parameters
    + turnir_id: 12 (required, number) - ID команды integer
    + season: 2016 (string) - сезон для выборки, передается год окончание сезона
    + tour_id: 12 (number) - ID турнира

+ Response 200 (application/json)

        {
            "seasons":{
                "2012":"2011/2012",
                "2015":"2014/2015",
                "2016":"2015/2016",
            },
            "tours":{
                123:"1-ый тур",
                12:"2-ой тур"
            },
            "games":[
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
        }
