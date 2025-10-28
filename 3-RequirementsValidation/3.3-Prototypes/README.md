Приклад 1 — Сторінка реєстрації
@startuml
skinparam backgroundColor #f0f8ff
skinparam rectangle {
  BackgroundColor #e6f2ff
  BorderColor #3399ff
  RoundCorner 15
}
skinparam note {
  BackgroundColor #fffacd
  BorderColor #ffcc00
}

component " Реєстрація" {
  [Логін]
  [Email]
  [Пароль]
  [Підтвердити пароль]
  [Кнопка Зареєструватися] as register_btn
}

note right of register_btn
  <b>Результати:</b>
  Повідомлення про успіх 
  Повідомлення про помилку 
end note 
Приклад 2 — Вхід користувача

@startuml
skinparam backgroundColor #f9fff0
skinparam component {
  BackgroundColor #ccffcc
  BorderColor #33cc33
  RoundCorner 12
}
skinparam note {
  BackgroundColor #fff0f5
  BorderColor #ff66cc
}

component " Авторизація" {
  [Логін]
  [Пароль]
  [Кнопка 'Увійти'] as login_btn
}

note right of login_btn
  При невірних даних показується повідомлення:
  "Невірний логін або пароль"
end note
@enduml

Приклад 3 — Сторінка профілю

@startuml
skinparam backgroundColor #fff8e1
skinparam rectangle {
  BackgroundColor #ffe0b3
  BorderColor #ff9933
  RoundCorner 15
}
skinparam note {
  BackgroundColor #e6ffe6
  BorderColor #33cc33
}

package " Профіль користувача" {
  [Ім’я користувача]
  [Кількість тренувань]
  [Кнопка 'Переглянути історію'] as history_btn
  [Кнопка 'Вихід'] as logout_btn
}

note right of history_btn
  Інформація про історію тренувань
end note

note right of logout_btn
  Кнопка для виходу з акаунту
end note
@enduml
