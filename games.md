# Матч-Центр
Информация о играх раздела Матч-Центр в API [Kairat](README.md)

## Список матчей
Получение списка матчей на определенную дату. Если дата не указана, то список игр на сегодня

### Получение списка [GET /games/{?date}]
+ Arguments
    + id: 21 (number) - ID турнира.
    + name: Примера (string) - название турнира
    + country: ES (string) - страна турнира
    + games:
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
            + logo: //img.kairat.kz/barcelona.png (string) -  ссылка на лого команды.
            + country: ES (string len=2) - IATA код страны команды.
            + cards - карточки
                + yellow: 2 (number) - желтые карты
                + red: 0 (number) - красные карты
            + corners: 2  (number) - угловые
        + guest: (Team) - вторая команда
            + id: 21 (number) - ID команды.
            + name: Рома (string) - название команды на русском.
            + logo: //img.kairat.kz/roma.png (string) -  ссылка на лого команды.
            + country: IT (string len=2) - IATA код страны команды.
            + cards - карточки
                + yellow: 2 (number) - желтые карты
                + red: 0 (number) - красные карты
            + corners: 2  (number) - угловые
+ Parameters
    + date: 2016.04.15 (optional, string) - ID команды integer
    
+ Response 200 (application/json)

        [
            {
                "id": 1,
                "name": "Примера",
                "country": "ES"
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
        ]

## Обзор матча
Информация по определенному матчу

### Описание матча [GET /game/{id}]
+ Arguments
    + turnir: 
        + id: 21 (number) - ID турнира.
        + name: Примера (string) - название турнира
        + country: ES (string) - страна турнира
    + games:
        + id: 11 (number) - ID матча.
        + dtime: 2016.02.05 20:00:00 (DateTime) - время проведения матча в формате YY.mm.dd H:m:s (? timezone UTC).
        + status: wait (string) - wait, live, cancel, fin
        + info:
            + score: 3-2 (string) - счет матча
            + part: 2 (number) - тайм
            + minute: 86 (number) - минута матча
            + place: Сюьдад де Валенсия (string) - стадион
            + judges: (Array) - судьи  матча
        + home: (Team) - первая команда
            + id: 22 (number) - ID команды.
            + name: Барселона (string) - название команды на русском.
            + logo: //img.kairat.kz/barcelona.png (string) -  ссылка на лого команды.
            + country: ES (string len=2) - IATA код страны команды.
            + cards - карточки
                + yellow: 2 (number) - желтые карты
                + red: 0 (number) - красные карты
            + corners: 2  (number) - угловые
        + guest: (Team) - вторая команда
            + id: 21 (number) - ID команды.
            + name: Рома (string) - название команды на русском.
            + logo: //img.kairat.kz/roma.png (string) -  ссылка на лого команды.
            + country: IT (string len=2) - IATA код страны команды.
            + cards - карточки
                + yellow: 2 (number) - желтые карты
                + red: 0 (number) - красные карты
            + corners: 2  (number) - угловые
        + text: (Array) - текстовая трансляция 
            + [минута, номер команды, событие, игрок]. События: SW-замена, YC-желтая карта, RC-красная карта, CR- угловой, GL-гол, PT-пенналти, AG-автогол,DN - удаление
        + feeds: (Array) - массив публикаций
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
            + title: (string) - заголовок статьи
            + descr: (string) - краткое описание статьи
            + body: (string) - сообщение
            + tags: (Array) - массив тегов к публикации
+ Parameters
    + id: 11 (required, integer) - ID матча 
+ Response 200 (application/json)

        {
            "id": 11,
            "time": "2016.02.05 20:00:00",
            "status" : "live",
            "turnir": {
                "id": 1,
                "name": "Примера",
                "country": "ES"
            },
            "info":{
                "score": "3:2",
                "part": 2,
                "minute": 86,
                "place": "Сюьдад де Валенсия",
                "judges":[
                    "Карлос Веласко Карбальо"
                ]
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
            "text":[
                [79,2,"SW","Набиль Эль-Жар","Давид Симон"],
                [76,2,"SW","Серхио Араухо","Тана Домингес"],
                [75,1,"SW","Джузеппе Росси","Жорди Шуметра"],
                [74,1,"YC","Жорди Шуметра"],
                [66,2,"GL","Виллиан Жозе"]
            ],
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
                    "title":"Re:старт. Как прошел 23-й тур КПЛ",
                    "descr":"Возобновление чемпионата Казахстана вышло довольно предсказуемым, но случилось одно исключение – матч-триллер в Актобе.",
                    "body":"<img src='//img.kairat.kz/feeds/u56sdf23gf.jpg'/>Русский форвард #Вашингтона оформил 14-й хет-трик за карьеру в НХЛ",
                    "tags": [
                        "Вашингтон"
                    ]
                }
            ]
        }   

## События матча
Получение текстовой трансляции матча - замены, голы, карточки 

### Трансляция матча [GET /game/{game_id}/text]
+ Argumnets
    + (Array)
        + (number) - минута матчка.
        + (number) - номер команды
        + (string) - тип события.
        + (string) - ФИО игрока.
        
+ Parameters
    + game_id: 12 (required, number) - ID команды integer

+ Response 200 (application/json)

        [
            [79,2,"SW","Набиль Эль-Жар","Давид Симон"],
            [76,2,"SW","Серхио Араухо","Тана Домингес"],
            [75,1,"SW","Джузеппе Росси","Жорди Шуметра"],
            [74,1,"YC","Жорди Шуметра"],
            [66,2,"GL","Виллиан Жозе"]
        ]

## Статистика
Получение статистики о предыдущих играх команд

### Статистика [GET /game/{game_id}/stats]
+ Argumnets
    + main: - основная статистика
        + (string) : (Array[2]) - заголовок строки : [значение хозеяв, значение для гостей]
    + groups: (Array) - дополнительная статистика
        + name: "Послдение игры Леванте" (string)  - название группы
        + type: (string) "tab" - тип группы. Может быть 3 типов - list,tabs и table 
        + tabs: (Array) - только если тип tab
            + name: "В сезоне"(string) - название таба
            + rows: (Array) - строки в табе
                + (Array[5]) - [id матча, дата, название команды 1, счет, название команды 2]
        +table: (Array) - только если тип table
            + (Array[10]) - [id команды, код страны, название команды, всего игр, выйграно, ничьи, проиграно, голов забито, голов пропущенно, очков]
+ Parameters
    + game_id: 12 (required, number) - ID команды integer

+ Response 200 (application/json)

        {
            "main":{
                "Матчей":[40,40],
                "Забитых мячей":[25,33],
                "Удары / в створ":["51/15","20/8"],
                "Угловые":[22,12]
            },
            "groups":[
                {
                    "name": "Послдение игры Леванте",
                    "type": "tab",
                    "tabs":[
                        {
                            "name":"В сезоне",
                            "rows":[
                                [123,"2016.01.05","Вестерн Сити","1:0","Леванте"],
                                [125,"2016.02.07","Леванте","3:2","Арсенал"],
                                [126,"2016.03.15","Арсенал","2:0","Леванте"],
                                [77,"2016.04.23","Вестерн Сити","3:1","Леванте"]
                            ]
                        },
                        {
                            "name":"В турнире",
                            "rows":[
                                [12,"2016.01.05","Вестерн Сити","1:0","Леванте"],
                                [23,"2016.02.07","Леванте","3:2","Арсенал"],
                                [56,"2016.03.15","Арсенал","2:0","Леванте"],
                                [18,"2016.04.23","Вестерн Сити","3:1","Леванте"]
                            ]
                        }
                    ]
                },
                {
                    "name": "Турнирная таблица",
                    "type": "table",
                    "table":[
                        [223,"ES","Вестерн Сити",16,9,3,4,16,9,30],
                        [125,"ES","Леванте",16,9,3,4,16,9,28],
                        [34,"ES","Арсенал",16,9,3,4,16,9,27],
                        [567,"ES","Вестерн Сити",16,9,3,4,16,9,20],
                        [12,"ES","Арсенал",16,9,3,4,16,9,19],
                        [67,"ES","Леванте Сити",16,9,3,4,16,9,6]
                    ]
                },
            ]
        }
        

## Составы
Информация о составах команд

### Состав [GET /game/{game_id}/list]
+ Arguments
    + coach - главный тренер.
        + home: (string) - тренер домашней команды
        + guest: (string) - тренер гостевой команды
    + in - Стартовые составы
        + home:(Array) - домашней команды - [ номер игрока, имя игрока, позиция]
        + guest:(Array) - гостевой команды - [ номер игрока, имя игрока, позиция]
    + substitution - Замены
        + home:(Array) - домашней команды - [ номер игрока, имя игрока, позиция]
        + guest:(Array) - гостевой команды - [ номер игрока, имя игрока, позиция]
    + injury - Травмированы / Точно не сыграют
        + home:(Array) - домашней команды - [ номер игрока, имя игрока, позиция]
        + guest:(Array) - гостевой команды - [ номер игрока, имя игрока, позиция]
    + Parameters
        + game_id: 12 (required, number) - ID команды integer
+ Значение позиции игроков:
    + C - Capitane ( капитан )
    + GK  - Goalkeeper ( вратарь )
    + SW  - Free Defender ( свободный защитник ) 
    + RB  - Right Defender ( правый защитник ) 
    + LB  - Left Defender ( левый защитник ) 
    + CB  - Central Defender ( центр защитник ) 
    + RWB  - Right Attacking Defender ( правый атакующий защитник ) 
    + LWB  - Left Attacking Defender ( левый атакующий защитник ) 
    + CDM  - Central Defensive Midfielder ( опорный/оборонительный полузащитник ) 
    + RM  - Right Midfielder ( правый полузащитник ) 
    + CM  - Central Midfielder ( центральный полузащитник ) 
    + LM  - Left Midfielder   ( левый полузащитник ) 
    + RWM  - Right Side Midfielder ( правый атакующий полузащитник ) 
    + LWM  -   Left Side Midfielder ( левый атакующий полузащитник ) 
    + CAM  - Central Attacking Midfielder ( центральный атакующий полузащитник ) 
    + RF  - Right Forward ( правый отянутый форвард ) 
    + CF  - Central Forward ( центральный отянутый форвард ) 
    + LF  - Left Forward ( левый отянутый форвард ) 
    + RS  - Right Striker ( правый конечный форвард ) 
    + LS  - Left Striker ( левый конечный форвард )
    + ST  - Striker ( центр форвард )
+ Parameters
    + game_id: 12 (required, number) - ID команды integer
    
+ Response 200 (application/json)

        {
            "coach":{
                "home":"Джузеппе Росси",
                "guest":"Серхио Араухо"
            },
            "in":{
                "home":[
                    [5,"Набиль Эль-Жар","C"],
                    [6,"Давид Симон","GK"],
                    [7,"Серхио Араухо","LB"],
                    [8,"Джузеппе Росси","LWM"],
                    [10,"Жорди Шуметра","RS"],
                    [2,"Виллиан Жозе","ST"]
                ],
                "guest":[
                    [5,"Набиль Эль-Жар","C"],
                    [6,"Давид Симон","GK"],
                    [7,"Серхио Араухо","CAM"],
                    [8,"Джузеппе Росси","CDM"],
                    [10,"Жорди Шуметра","CF"],
                    [2,"Виллиан Жозе","LS"]
                ]
            },
            "substitution":{
                "home":[
                    [5,"Набиль Эль-Жар","C"],
                    [6,"Давид Симон","GK"],
                    [7,"Серхио Араухо","ST"],
                    [8,"Джузеппе Росси","D"],
                    [10,"Жорди Шуметра","P"],
                    [2,"Виллиан Жозе","W"]
                ],
                "guest":[
                    [5,"Набиль Эль-Жар","CAM"],
                    [6,"Давид Симон","GK"],
                    [7,"Серхио Араухо","ST"],
                    [8,"Джузеппе Росси","D"],
                    [10,"Жорди Шуметра","GK"],
                    [2,"Виллиан Жозе","W"]
                ]
            },
            "injury":{
                "home":[
                    [5,"Набиль Эль-Жар","C"],
                    [6,"Давид Симон","GK"]
                ],
                "guest":[
                    [5,"Набиль Эль-Жар","C"]
                ]
            }
        }
        
## Медиа
Медиа материалы к матчу

### Медиа [GET /game/{game_id}/media]
+ Arguments
    + photos: (Array) - фото к матчу
    + videos: (Array) - видео к матчу
    + gifs: (Array) - gifs к матчу
        
+ Parameters
    + game_id: 12 (required, number) - ID команды integer
    
+ Response 200 (application/json)

        {
            "photos":[
                {
                    "id":123,
                    "thumb":"//img.kairat.kz/photos/sdf34rf.jpg",
                    "src":"//img.kairat.kz/photos/sdf34rf_big.jpg",
                }
            ],
            "videos":[
                {
                    "id":123,
                    "thumb":"//img.kairat.kz/photos/sdf34rf.jpg",
                    "src":"//img.kairat.kz/photos/sdf34rf.mp4",
                }
            ],
            "gifs":[
                {
                    "id":123,
                    "thumb":"//img.kairat.kz/photos/sdf34rf.jpg",
                    "src":"//img.kairat.kz/photos/sdf34rf.gif",
                }
            ],
        }
