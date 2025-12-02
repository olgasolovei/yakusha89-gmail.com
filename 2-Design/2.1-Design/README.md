@startuml

class Sensor {
    - id: int
    - loadValue: double
    - wearLevel: double
    - usageFrequency: double
    + readLoad(): double
    + readWear(): double
}


class RiskAnalyzer {
    - threshold: double
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
    - data: List<RiskEvent>
    + exportPDF()
}


Sensor --> RiskAnalyzer : дані
RiskAnalyzer --> RiskEvent : створює
RiskAnalyzer --> Notifier : надсилає оповіщення
RiskAnalyzer --> Logger : логування
RiskAnalyzer --> EmergencyStop : критичний ризик
Logger --> ReportGenerator : дані для звітів
ReportGenerator --> Report

@enduml
