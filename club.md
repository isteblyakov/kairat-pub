# Клуб
Информация о клубе в API [Kairat](README.md)

## История клуба
История и достижения клуба

### История [GET /club]
+ Arguments
    + history: (string) - история клуба .
    + achievements: (string) - достижения клуба

+ Response 200 (application/json)

            {
                "history": "<img src='//img.kairat.kz/feeds/u56sdf23gf.jpg'/><h1>1995 год – Основание клуба</h1>1995 год – Основание клуба Группа амибициозных любителей мини-футбола открыла клуб под названием Кайнур, который в будущем станет известным как один из самых сильных топовых клубов мира. Сегодня алматинский Кайрат регулярно побеждает на национальном чемпионате последние десять лет и входит в число лучших команд Европы.",
                "achievements":"<h1>2014 - СУПЕРКУБОК МИРА</h1> Четыре сильнейшие команды со всего света оспаривали звание лучшего на планете – но в конечном итоге все свелось к ставшему уже классическим противостоянию Кайрата и московского Динамо."
            }
        
## Состав
Состав команды

### Описание команды [GET /club/team]
+ Arguments
    + admins: (Array) - администрация клуба
        + id:  (number) - ID
        + name: (string) - ФИО
        + title: (string) - должность
        + thumb: (string) - адрес к аватарке
    + treners: (Array) - тренерский штаб клуба
        + id:  (number) - ID
        + name: (string) - ФИО
        + title: (string) - должность
        + thumb: (string) - адрес к аватарке 
    + team: (Array) - игроки клуба
        + id:  (number) - ID
        + name: (string) - ФИО
        + title: (string) - позиция на поле
        + captain: (boolean) - кабитан да / нет
        + number: (number) - игровой номер
        + thumb: (string) - адрес к аватарке 

+ Parameters
    + team_id: 12 (required, number) - ID команды integer

+ Response 200 (application/json)

        {
                "admins":[
                    {
                        "id":12,
                        "name": "Ануар Оразбеков",
                        "title":"Вице-президент",
                        "thumb":"//img.kairat.kz/admins/u12.jpg"
                    }
                ],
                "treners":[
                    {
                        "id":11,
                        "name": "РИКАРДО КАМАРА СОБРАЛ",
                        "title":"Главный тренер",
                        "thumb":"//img.kairat.kz/treners/u11.jpg"
                    }
                ],
                "team":[
                    {
                        "id":9,
                        "name": "ДИНМУХАМБЕТ СУЛЕЙМЕНОВ",
                        "title":"ЗАЩИТНИК",
                        "captain": "true",
                        "number": 8,
                        "thumb":"//img.kairat.kz/team/u11.jpg"
                    }
                ]
        }   

        
## Игрок
Подробное описание игрока / тренера

### Игрок [GET /club/team/{id}]
+ Arguments
    + id:  (number) - ID
    + name: (string) - ФИО
    + title: (string) - позиция на поле
    + captain: (boolean) - кабитан да / нет
    + number: (number) - игровой номер
    + thumb: (string) - адрес к аватарке 
    + birthday: (Date) - дата рождения в формате Y.m.d  
    + height: (number) -рост в см
    + weight: (number) - вес в кг
    + contract: (number) - контракт до какого года
    + photos: (Array) - массив адресов к фото
    + body: (string) - описание игрока / достижения
    
+ Parameters
    + id: (required, number) - ID игрока integer

+ Response 200 (application/json)

        
            {
                "id":9,
                "name": "ДИНМУХАМБЕТ СУЛЕЙМЕНОВ",
                "title":"ЗАЩИТНИК",
                "captain": "true",
                "number": 8,
                "thumb":"//img.kairat.kz/team/u11.jpg"
                "birthday": "2016.01.05",
                "height": 182,
                "weight": 79,
                "mainleg": "right",
                "contract": 2016,
                "photos":[
                  "//img.kairat.kz/team/u1sdfsdf1.jpg",
                  "//img.kairat.kz/team/gfdfg.jpg",
                  "//img.kairat.kz/team/uasdfwe23411.jpg"
                ],
                "body":"Чемпион Казахстана — (2009/2010, 2010/11, 2011/12, 2012/13, 2013/14, 2014/15, 2015/16)<br>Обладатель Кубка Казахстана — (2009/2010, 2010/11, 2011/12, 2012/13, 2013/14, 2014/15, 2015/16)<br>",
            }  
        
        
