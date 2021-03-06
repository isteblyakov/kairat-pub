# Статистика
Описание методов раздела Статиска API [Kairat](README.md)

## Турнирная таблица
Возвращает турнирную таблицу, список доступных турниров и сезонов.

### Список [GET /club/turnir/{?turnir_id}/{?season}]
+ Arguments
    + id: (number) - номер турнира   
    + name: (string) - название группы.
    + icon: (string) - адрес иконки группы
    + seasons: (Object) - список доступных сезонов
        + value: name - номер сезона / название сезона
    + table: (Array)
        + name: (Array) - название этапа
        + type: table (string) - тип этапа
    
            Если этап 1 группа (например чемпионат страны), то:
            + data: (Object)
                + tableName: (Array) - название таблицы
                    + (Array[10]) - [id команды, код страны, название команды, всего игр, выйграно, ничьи, проиграно, голов забито, голов пропущенно, очков]               
    
            Если этап состоит из несколькоих групп (груповой этап в Лиге Чемпионов, Лиге Европе и т.д.), то:
            + data: (Object)
                + group (Array) - список групп
                    + (Array[10]) - [id команды, код страны, название команды, всего игр, выйграно, ничьи, проиграно, голов забито, голов пропущенно, очков]
    
            Если этап плэй-офф (игры на выбывание)
            + data: (Object)
                + subStageName : (Array) - список матчей на данной части плэй-оффа (например 1/8 финала)
                    + (Array[4]) - [id матча, id команды хозяев, id команды гостей, счёт]

+ Parameters
    + turnir_id: 12 (number) - ID турнира integer
    + season: 2016 (string) - сезон для выборки, передается год окончания сезона

+ Response 200 (application/json)

        {
            "id": "1",
            "name": "Чемпионат Казахстана - Высшая Лига",
            "seasons":{
                "2015":"2015",
                "2016":"2016",
            },
            "season":"2015/2016",
            "table": [
                {
                    "name": "Турнир за 1-6 места",
                    "type" : "table",
                    "data : {
                        "Основная таблица":[
                            [223,"KZ","Кайрат",16,9,3,4,16,9,30],
                            [125,"KZ","Аят",16,9,3,4,16,9,28],
                            [34,"KZ","Актобе",16,9,3,4,16,9,27],
                            [567,"KZ","Астана-Тулпар",16,9,3,4,16,9,20]
                        ],
                        "Последние 5 туров":[
                            [223,"KZ","Кайрат",16,9,3,4,16,9,30],
                            [125,"KZ","Аят",16,9,3,4,16,9,28],
                            [34,"KZ","Актобе",16,9,3,4,16,9,27],
                            [567,"KZ","Астана-Тулпар",16,9,3,4,16,9,20]
                        ]
                    }
                },
                {
                    "name": "Турнир за 7-12 места",
                    "type" : "table",
                    "data : {
                        "Основная таблица":[
                            [223,"KZ","Кайрат",16,9,3,4,16,9,30],
                            [125,"KZ","Аят",16,9,3,4,16,9,28],
                            [34,"KZ","Актобе",16,9,3,4,16,9,27],
                            [567,"KZ","Астана-Тулпар",16,9,3,4,16,9,20]
                        ],
                        "Последние 5 туров":[
                            [223,"KZ","Кайрат",16,9,3,4,16,9,30],
                            [125,"KZ","Аят",16,9,3,4,16,9,28],
                            [34,"KZ","Актобе",16,9,3,4,16,9,27],
                            [567,"KZ","Астана-Тулпар",16,9,3,4,16,9,20]
                        ]
                    }
                }
            ]
        },
        {
            "id": "160",
            "name": "Лига чемпионов",
            "seasons": [
                 "2016" : 2015/2016",
            ],
            "table": [
                 {
                     name: "Групповой этап",
                     type: "groups",
                     data: {
                         Группа A: [
                             [
                                 "363",
                                 "Реал Мадрид",
                                 "6",
                                 "5",
                                 "1",
                                 "0",
                                 "19",
                                 "3",
                                 "16"
                             ],
                             [
                                 "445",
                                 "ПСЖ",
                                 "6",
                                 "4",
                                 "1",
                                 "1",
                                 "12",
                                 "1",
                                 "13"
                             ],
                             [
                                 "110",
                                 "Шахтер",
                                 "6",
                                 "1",
                                 "0",
                                 "5",
                                 "7",
                                 "14",
                                 "3"
                             ],
                             [
                                 "1605",
                                 "Мальме",
                                 "6",
                                 "1",
                                 "0",
                                 "5",
                                 "1",
                                 "21",
                                 "3"
                             ]
                         ],
                         Группа B: [...],
                         Группа C: [...],
                         Группа D: [...],
                         ...,
                     }
                 },
                 {
                     "name": "Плэй-офф",
                     "type": "playoff",
                     "data": {
                         "1/8 финала": [
                             [
                                 "3",
                                 "ПСЖ",
                                 "Челси",
                                 "2-1"
                             ],
                             [
                                 "4",
                                 "Челси",
                                 "ПСЖ",
                                 "1-2"
                             ]
                         ],
                         "1/4 финала": [
                             [
                                 "5",
                                 "ПСЖ",
                                 "Манчестер Сити",
                                 "2-2"
                             ],
                             [
                                 "6",
                                 "Манчестер Сити",
                                 "ПСЖ",
                                 "1-0"
                             ]
                         ],
                         "1/2 финала": [...],
                         "финал": [...]
                     }
                 }
             ]
        }


