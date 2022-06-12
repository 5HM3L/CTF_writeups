# VolgaCTF 2022 Qualifier 
##  Login Page

Для решения удобнее всего использовать [BurpSuite](https://portswigger.net/burp)

Задача состоит в том, чтобы залогиниться за пользователя admin через предложенную форму регистрации.

- Запускаем Burp, переходим на вкладку Proxy -> Intercept, нажимаем кнопку Open Browser.

В открывшемся браузере в адресную строку вводим адрес таска: [https://login.volgactf-task.ru/](https://login.volgactf-task.ru/), видим форму входа/регистрации.

- Регистриуем нового пользователя 123321 с паролем 123321.

- Успешно авторизуемся, видим сообщение: 

``` You are not admin. Your id 710 ``` 

- Переходим во вкладку HTTP history и изучаем ответы сервера. 

Внимание привлекают куки последнего запроса к серверу:

``` Cookie: login=s%3A123321.VqNsR3zPEwbWa0wVYapUY5cjzd5LL0v%2FleY9JNSuKZQ; password=s%3A123321.VqNsR3zPEwbWa0wVYapUY5cjzd5LL0v%2FleY9JNSuKZQ ```

123321 - это наш логин, что если поменять его на admin ? 

- Щелкаем правой кнопкой мыши на наш последний запрос, нажимем Ctrl+R (команда Send to Repeater)

- Переходим во вкладку Repeater, там в окне Request видим наш запрос, доступный для редактирования.

Меняем 123321 на admin и посылаем запрос серверу (кнопка Send), получаем ответ:

``` Welcome admin. Your flag VolgaCTF{9fd3c2193cc87bbc16e34c563a35584d} ```










