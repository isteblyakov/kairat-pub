# Group Команда
Информация о команде в API [Prosports](README.md)

## Список команд
Возвращает список команд по группам

### Список [GET /teams]
+ Arguments
    + name: Национальные (string) - название группы.
    + groups: (Array) - список подгрупп
    + icon: "//img.neverbet.com/country/EN.png" (string) - адрес иконки группы
    + teams: (Array) - список команд в группе/подгруппе
        + id: 12 (number) - ID команды.
        + name: Барселона (string) - название команды на русском.
        + logo: //img.neverbet.com/mini/barcelona.png (string) - ссылка на лого команды.

+ Response 200 (application/json)

        [
            {
                "name": "Популярные",
                "teams":[
                    {
                        "id" : 12,
                        "name": "Барселона",
                        "logo": "//img.neverbet.com/team/mini/barcelona.png",
                    }
                ]
            },
            {
                "name": "Национальные",
                "groups":[
                    {
                        "name": "Англия",
                        "icon": "//img.neverbet.com/country/EN.png",
                        "teams":[
                            {
                                "id" : 12,
                                "name": "Барселона",
                                "logo": "//img.neverbet.com/team/mini/barcelona.png",
                            }
                        ]
                    }
                ]
            }
        ]
        
## Команда
Подробное описание команды

### Описание команды [GET /team/{team_id}]
+ Arguments
    + id: 12 (number) - ID команды.
    + name: Барселона (string) - название команды на русском.
    + original: Barcelona (string) - оригинальное название команды.
    + rating: 6.8 (number) - рейтинг команды.
    + country: ES (string len=2) - IATA код страны команды.
    + city: Барселона (string) - город в котором базируется команда.
    + coach: Луис Энрике (string) - тренер команда.
    + arena: Камп Ноу (string) - домашняя арена команды.
    + based: 1899.11.23 (Date) - дата основания команды в формате Y.m.d
    + logo: //img.neverbet.com/team/barcelona.png (string) - ссылка на лого команды.
    + status: WLDWW (string) - статистика по последним 5 играм. W (win) - побед,  L(lose) - поражений, D(draw) - ничьи.
    + stats: (Object) - статистика
        + name (string): value (string) - название : значение
    + games: (Array) - прошедшие 5 игр команды
        + id: 12 (number) - ID номер матча 
        + dtime: 2016.01.05 20:30 (DateTime) - дата и время начала матча в формате Y.m.d H:m 
        + home: Вестерн Сити (string) - название домашней команды 
        + score:(string) - счет в матче
        + guest: (string) - название команды гостей
    + feeds: (Array) - последние новости/публикации по команде
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
    + team_id: 12 (required, number) - ID команды integer

+ Response 200 (application/json)

        {
                "id" : 12,
                "name": "Барселона",
                "original": "Barcelona",
                "rating": 6.8,
                "country": "ES",
                "city": "Барселона",
                "coach": "Луис Энрике",
                "arena": "Камп Ноу",
                "based": "1899.11.23",
                "logo": "//img.neverbet.com/team/barcelona.png",
                "status": "WLDWW",
                "stats":{
                    "матчи": 32,
                    "гол / матч": 1.1,
                    "желтые карточки": 2,
                    "красные карточки": 3,
                    "угловые": 12
                },
                "games":[
                    {
                        "id":12,
                        "dtime": "2016.01.05 20:30",
                        "home":"Вестерн Сити",
                        "score":"1:0",
                        "guest":"Леванте"
                    }
                ],
                "feeds":[
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
        }   

        
## Новости
Новости/публикации по команде

### Новости команды [GET /team/{team_id}/feeds/{?offset}]
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
    + team_id: 12 (required, number) - ID команды integer
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
        
## Состав
Состав команды по группам

### Состав команды [GET /team/{team_id}/list]
+ Arguments
    + (string) : (Array) - название группы игроков
        + id: (number) - ID игрока
        + number:  (number) - игровой номер игрока
        + name: (string) - имя игрока
        + thumb: (string) - адрес к фото игрока
        + games: (number) - кол-во игр в которых принял участие игрок
        + goals: (number) - кол-во забитых голов 
        + missed: (number) - кол-во пропущенных голов

+ Parameters
    + team_id: 12 (required, number) - ID команды integer

+ Response 200 (application/json)

        {
            "Вратарь":[
                {
                    "id":22,
                    "number":7,
                    "name":"Эндрю Редмейн",
                    "thumb":"//img.neverbet.com/football/g22.jpg",
                    "games":16,
                    "goals":2,
                    "missed":0
                }
            ],
            "Защитник":[
                {
                    "id":23,
                    "number":6,
                    "name":"Брендан Хэмилл",
                    "thumb":"//img.neverbet.com/football/g22.jpg",
                    "games":16,
                    "goals":2,
                    "missed":0
                }
            ]
        }

## Таблица
Турнирные таблицы турниров в которых принимает участие команда
Если не задан сезон и турнир, возвращает все турниры на данный сезон

### Турнирная таблица [GET /team/{team_id}/table/{?season}{?turnir_id}]
+ Arguments
    + turnir: (Turnir) -
        + id: (number) - ID турнира
        + name: (string) - название турнира
        + country: (string) - IATA код страны
    + seasons: (Object) - список доступных сезонов
        + value: name - номер сезона / название сезона
    + season: (string) - название сезона
    + table: (Object)
        + name : (Array) - название таблицы
            + (Array[10]) - [id команды, код страны, название команды, всего игр, выйграно, ничьи, проиграно, голов забито, голов пропущенно, очков]
        

+ Parameters
    + team_id: 12 (required, number) - ID команды integer
    + season: 2016 (string) - сезон для выборки, передается год окончание сезона
    + turnir_id: 12 (number) - ID турнира

+ Response 200 (application/json)

        [
            {
               "turnir":{
                    "id":12,
                    "name": "Примьер Лига",
                    "country": "UK"
               },
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
        ]
        
## Матчи
Матчи в которых команда принимает/принимала участие

### Матчи [GET /team/{team_id}/games/{?season}{?turnir_id}]
+ Arguments
    + turnirs: (Object)  - список доступных турниров
        + value: name - номер турнира / название турнира
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
        + odds - ставки / коэффициенты
            + P1 : 1.2 (float) - победа первой команды 
            + X: 2.2 (float) - ничья 
            + P2: 2.0 (float) - победа второй команды 
            + TOTAL: (Object)  - тотал
                "2.5": (Array[2]) - значение [больше чем значение, меньше чем значение] 
    
+ Parameters
    + team_id: 12 (required, number) - ID команды integer
    + season: 2016 (string) - сезон для выборки, передается год окончание сезона
    + turnir_id: 12 (number) - ID турнира

+ Response 200 (application/json)

        {
            "seasons":{
                "2012":"2011/2012",
                "2015":"2014/2015",
                "2016":"2015/2016",
            },
            "turnirs":{
                123:"Испания. Примера",
                12:"Чемпионат Испании"
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
                    },
                    "odds":{
                        "P1": 1.2,
                        "X": 2.2,
                        "P2": 2.0,
                        "TOTAL": {
                            "2.5":[1.2,3.2]
                        }
                    }
                }
            ]
        }
