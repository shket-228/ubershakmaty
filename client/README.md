# Описание страниц и готовых функций

## Верхний колонтитул header

`Header.jsx` - интерфейс верхнего колонтитула

На этой панеле, расположенной сверху страницы, находятся: аватарка пользователя, его никнейм, статус активности, а также панель перехода на другие страницы, которая содержит ссылку на личный кабинет пользователя, на главную страницу приложения, на страницу настроек.

---

## Главная страница

`MainPageGame.jsx` - интерфейс главной страницы приложения

На главной странице отрисованы три панели: новая игра, игра с друзьями, посмотреть таблицу лидеров.
На панеле "новая игра" находится кнопка, начинающая игру, которую в дальнейшем планируется соединить с соответствующей функциональностью. Также на этой панеле расположена кнопка `DropDownButton.jsx`, которая открывает панель выбора типа игры `DropDownPanel.jsx` при нажатии. На этой выпадающей панели расположены три возможных режима: Блиц, Рапид, Пуля. Под каждым режимом находятся кнопки `GameModeButton.jsx` с разной продолжительностью или типом игры.

---
## Страница шахматной доски

`Board.jsx` - интерфейс шахматной доски

В Board.jsx есть все необходимые составляющие, начиная от самой доски, заканчивая прикрепленным к ней фигурам. К доске прикреплены часы, со временем Clock.jsx, в котором отсчет времени у каждого игрока до 500 секунд. Пока играет человек за черные фигуры, отсчет времени происходит у него. Как только право хода перешло человеку, который играет за белые фигуры, отсчет времени останавливается. И аналогично начинается у человека, играющего за белые фигуры. Кроме того, к странице доски подключен Header.jsx, который сможет переадресовать вас на необходимые страницы, такие как "Главная",  "Игра", "Рейтинг", "Войти"

---
## Страница таблицы лидеров

`Table.jsx` - интерфейс таблицы лидеров

На данной странице можно посмотреть, кто занимает лидирующие позиции, в которой каждый из пользователей имеет свой "Rang", "Rating", "Name", "Month-Year", "Country". Кроме того, к странице доски подключен Header.jsx, который сможет переадресовать вас на необходимые страницы, такие как "Главная",  "Игра", "Рейтинг", "Войти"

---
## Статистика

`Statistic.jsx` - интерфейс страницы статистики пользователя

На этой странице находятся две панели: информация о поледних партиях и общая статистика по количеству партий. Оформлены они в виде таблиц. Таблица информации о последних партиях содержит следующие поля: оппонент, результат, ходы и дата. Таблица общей статистики содержит информацию о количестве проведенных партий для каждого типа игры.

---
## Настройки

`Settings.jsx` - интерфейс страницы настроек

Данная страница разделена на две части, составляющие настройки профиля: обновление непосредственно самого профиля, где можно изменить ник и возраст, и обновление пароля, где нужно ввести старый пароль, затем новый и еще раз новый. Кроме того, к странице настройки подключен Header.jsx, который сможет переадресовать вас на необходимые страницы, такие как "Главная",  "Игра", "Рейтинг", "Войти".

---
## Регистрация

`Register.jsx` - интерфейс страницы регистрации

На странице регистрации предлагается ввести свое имя, электронную почту, пароль, а затем подтвердить пароль. Также информируется, что данная игра подходит для всех уровней: для новичков, начального, среднего и Pro. После чего можно зарегистрироваться. Также можно зарегистрироваться через свой Google, Apple или Facebook аккаунты. Если же аккаунт уже имеется, предлагается перейти на страницу входа. 

---
## Вход

`Login.jsx`- интерфейс страницы входа

Данная страница отвечает за вход, посредством введения логина и пароля. Также вход можно осуществить через свой Google, Apple или Facebook аккаунты. Если же аккаунт не создан, есть возможность создать его, нажав кнопку "Зарегистрироваться". 

<br />
<br />

# Запросы / сервисы

## `AuthServices.js`
Функции, отправляющие HTTP запросы к серверу для осуществления авторизации, используются в экшонах `authReducer`
- `register(credentials)` регистрация, возвращает response body
- `login(credentials)` логин, возвращает response body
- `logout()` логаут, ничего не возвращает
- `refreshTokens()` обновление токенов, возвращает response body


# Redux редюсеры

## `requestReducer.js`
Отвечает за обработку запросов
### States
- `error` - ошибка, возвращаемая беком
- `isLoading` - состояние выполнения запроса: `true`, значит выполняется
### Actions
- `requestAction(requestCallback)` обертка для запросов, обновляет `error` и `isLoading`
- `clearErrorsAction()` очищает сообщения об ошибке: `error` $\rightarrow$ `null`

## `authReducer.js`
Редюсер для JWT авторизации
### States
- `authUser` - объект авторизированного пользователя
- `accessToken` - строковое представление токена доступа
### Actions
Соответствующие функции авторизации, обновляющие стейты
- `registerAction(credentials)`
- `loginAction(credentials)`
- `logoutAction()`
- `refreshTokensAction()`

