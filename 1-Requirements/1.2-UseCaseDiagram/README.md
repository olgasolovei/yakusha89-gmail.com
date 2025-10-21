@startuml
left to right direction
skinparam packageStyle rectangle
skinparam usecase {
  BackgroundColor LightBlue
  BorderColor DarkBlue
}

actor "Інженер з безпеки" as SafetyEng
actor "Кінцевий користувач (Safety Engineer)" as EndUser
actor "QA Team" as QA
actor "Фахівець з ML/AI" as MLExpert
actor "Керівник проєкту" as PM
actor "Система IoT" as IoT

package "Система виявлення ризиків на майданчику" {

  usecase "UC-01: Моніторинг стану\nпідйомного обладнання" as UC1
  usecase "UC-02: Сповіщення працівників\nпро небезпечну ситуацію" as UC2
  usecase "UC-03: Візуалізація стану ризиків" as UC3
  usecase "UC-04: Генерація звітів про ризики" as UC4

  SafetyEng --> UC1
  SafetyEng --> UC2
  EndUser --> UC2
  EndUser --> UC3
  QA --> UC2
  MLExpert --> UC1
  PM --> UC1

  UC1 --> UC2 : include
  UC2 --> UC3 : include
  UC4 --> UC3 : include
}

@enduml
