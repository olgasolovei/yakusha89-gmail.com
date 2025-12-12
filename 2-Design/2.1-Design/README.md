 @startuml
title Система моніторингу та аналізу ризиків з інтерфейсом сенсорів

interface SensorInterfaceManager {
  + configureSensor(sensorId: int, settings: Map)
  + calibrateSensor(sensorId: int)
  + startMonitoring(sensorId: int)
  + stopMonitoring(sensorId: int)
}

class Sensor {
  - id: int
  - loadValues: Array
  - wearLevels: Array
  - usageFrequencies: Array
  + readLoad(): double
  + readWear(): double
}

class RiskAnalyzer {
   - thresholds: Array
  + analyze(sensor: Sensor): RiskEvent
}

class RiskEvent {
  - id: int
  - timestamp: Date
  - level: String
  - sensorId: int
}

class Notifier {
  + sendAlert(event: RiskEvent)
}

class Logger {
  + logEvent(event: RiskEvent)
}

class EmergencyStop {
  + stopMechanism()
}

class ReportGenerator {
  + generateReport(start: Date, end: Date): Report
}

class Report {
  - data: List
  + exportPDF()
}

' Зв'язки
SensorInterfaceManager -- Sensor : керує/взаємодіє

Sensor --> RiskAnalyzer : надає дані (readLoad/readWear)
RiskAnalyzer --> RiskEvent : створює
RiskAnalyzer --> Notifier : надсилає оповіщення
RiskAnalyzer --> Logger : логування
RiskAnalyzer --> EmergencyStop : критичний ризик
Logger --> ReportGenerator : дані для звітів
ReportGenerator --> Report : створює

@enduml
