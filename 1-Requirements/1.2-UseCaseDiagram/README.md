@startuml
left to right direction
skinparam packageStyle rectangle
skinparam usecase {
  BackgroundColor LightBlue
  BorderColor DarkBlue
}

actor "Інженер з безпеки" as SafetyEng
actor "Кінцевий користувач (працівник)" as EndUser
actor "QA Team" as QA
actor "Фахівець з ML/AI" as MLExpert
actor "Керівник проєкту" as PM
actor "Система IoT" as IoT

package "Система виявлення ризиків на майданчику" {

  usecase "UC-01: Моніторинг стану\nпідйомного обладнання" as UC1
  usecase "UC-02: Сповіщення працівників\nпро небезпечну ситуацію" as UC2
  usecase "UC-03: Візуалізація стану ризиків" as UC3
  usecase "UC-04: Генерація звітів про ризики" as UC4
  usecase "UC-05: Налаштування параметрів сенсорів" as UC5
  usecase "UC-06: Оновлення моделей ML/AI" as UC6
  usecase "UC-07: Перевірка та тестування системи" as UC7
  usecase "UC-08: Впровадження системи на майданчику" as UC8

   SafetyEng --> UC1
  SafetyEng --> UC2
  SafetyEng --> UC5
  SafetyEng --> UC4
  EndUser --> UC2
  EndUser --> UC3
  QA --> UC7
  MLExpert --> UC6
  PM --> UC8

   UC1 --> UC2 : include
  UC2 --> UC3 : include
  UC4 --> UC3 : include
  UC5 --> UC1 : extend
  UC6 --> UC1 : extend
  UC7 --> UC1 : extend
  UC8 --> UC1 : include
  UC8 --> UC2 : include
}

@enduml
