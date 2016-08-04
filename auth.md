# Авторизация
Описание методов авторищации к API [Prosports](README.md)
> Для получениея доступа к методам API необходимо передавать токен доступа в заголовке X-Access-Token с каждым запросом  к серверу


##  Авторизация
### Авторизация [POST /auth]
+ Arguments

    + login:  (string) - допускаются символы "A-Za-z0-9._" мин длина 3 симв макс символов 100
    + password: (string) - допускаются символы "A-Za-z0-9._!@#$%^&*" мин длина 6 симв макс символов 100
+ Request 

    + Body
    
            login: test
            password: "qwerty"

+ Response 200 (application/json)

    + Attributes (object)
            refresh (string) - ключ для обновления токена
            id (number) - ID пользователя
            X-Access-Token (string) - токен доступа к API

    + Headers
    
            X-Access-Token: fc5b2b8360c3e2155c336c24a0c19650
    
    + Body

            {
                "refresh": "3d9fff0420e63f8b6382d4ea6897b468",
                "rating": 0,
                "city": null,
                "status": null,
                "id": 2,
                "thumb": "https://lh5.googleusercontent.com/-jXdw6robJ50/AAAAAAAAAAI/AAAAAAAAAQ4/BNv5oiatbMk/photo.jpg",
                "bets": 0,
                "name": "Dmitriy Alexashov",
                "rate": 2,
                "country": null
            }

### Регистрация пользователя [PUT /auth]
+ Arguments

    + login:  (string) - допускаются символы "A-Za-z0-9._" мин длина 3 симв макс символов 100
    + email: (string) - 
    + password: (string) - допускаются символы "A-Za-z0-9._!@#$%^&*" мин длина 6 симв макс символов 100
    + token: (required, string) - токен мобильного устройства
    + device: (required, string) - код мобилльного устройства. Для айфона должно начинаться с "iphone". Для андройда начинается с "androind". Далее может быть информация о версии 
    + dummy:  (string) - флаг первичной регистрации. Если указан в запросе игнорируется все поля кроме token и device
+ Request 

    + Body
    
            login: test
            email: "test@test.com"
            password: "qwerty"
            token: "b2b8360c3e2155c336c24a0c19b2b8360c3e2155c336c24a0c19b2b8360c3e2155c336c24a0c19"
            device: "iphone 5s 8.1"
        
+ Response 200 (application/json)

    + Attributes (object)
            refresh (string) - ключ для обновления токена
            id (number) - ID пользователя
            X-Access-Token (string) - токен доступа к API

    + Headers
    
            X-Access-Token: fc5b2b8360c3e2155c336c24a0c19650
    
    + Body

            {
                "refresh":"4f293cfb66006bdd24b1a9a72f835333",
                "id":22
            }  

### Выход [DELETE /auth]
+ Arguments

    + key:  (string) - ключ для обновления токена
    + X-Access-Token (string) - токен доступа к API

+ Request 

    + Headers
    
            X-Access-Token: fc5b2b8360c3e2155c336c24a0c19650

    + Body
    
            key: "4f293cfb66006bdd24b1a9a72f835333"

        
+ Response 200 (application/json)


    + Body

            {
                "status":"ok"
            }  

##  Авторизация Google 

### Авторизация пользователя [GET /auth/google]

+ Arguments
    + refresh (string) - ключ для обновления токена
    + id (number) - ID пользователя
    + X-Access-Token (string) - токен доступа к API
    + rating (number) - рейтинг пользователя
    + status (string) - статус последних 5 ставок 
    + country (string) - страна
    + city (string) - город
    + thumb (string) - путь к аватарке пользователя
    + rate (number) - рейтинг пользователя
    + bets (number)- кол-во ставок
    + name (string) - имя пользователя


+ Response 200 (application/json)

    + Headers
    
            X-Access-Token: fc5b2b8360c3e2155c336c24a0c19650
    
    + Body

            {
              "rating": 0,
              "status": null,
              "country": null,
              "city": null,
              "thumb": "https://lh5.googleusercontent.com/-jXdw6robJ50/AAAAAAAAAAI/AAAAAAAAAQ4/BNv5oiatbMk/photo.jpg",
              "rate": 2,
              "bets": 0,
              "id": 2,
              "refresh": "3c80695cd9eff8714486a9e095bf6444",
              "name": "Dmitriy Alexashov"
            }
