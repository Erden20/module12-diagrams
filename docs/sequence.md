sequenceDiagram
    autonumber
    participant Manager as Руководитель
    participant HR as HR
    participant Candidate as Кандидат
    participant System as Система
    participant IT as IT-отдел

    Manager->>HR: Отправляет заявку на вакансию
    HR->>HR: Проверяет соответствие заявки требованиям
    alt Заявка корректна
        HR->>Manager: Утверждает заявку
        HR->>System: Публикует вакансию на сайте
        Candidate->>System: Подает заявку
        System->>HR: Отправляет анкету кандидата
        HR->>Candidate: Приглашение на собеседование
        HR->>Manager: Передает на техническое интервью
        Manager->>Candidate: Проводит техническое интервью
        alt Собеседование успешно
            HR->>Candidate: Предлагает оффер
            Candidate->>HR: Подтверждает оффер
            HR->>System: Добавляет сотрудника в базу
            HR->>IT: Уведомляет о настройке рабочего места
        else Отказ
            HR->>Candidate: Сообщает об отказе
        end
    else Заявка не корректна
        HR->>Manager: Возврат на доработку
    end
