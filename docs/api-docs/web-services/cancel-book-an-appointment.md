---
sidebar_position: 6
---

# CancelBookAnAppointment (отмена записи)

## Описание

```text
CancelBookAnAppointment(GUID[string], AdditionalInformation[string], Reason[string])
```

`GUID` – уникальный идентификатор заявки.

> У заявки ставится «Пометка на удаление», состояние заявки меняется на «Отменена».

## Возможные ошибки

1. Ошибка при получении уникального идентификатора на основе GUID.
2. Ошибка при выполнении поиска заявки по уникальному идентификатору.
3. Не удалось записать документ Заявка.

## Пример запроса

```xml title="Тело запроса"
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
    <soap:Body>
        <ru:CancelBookAnAppointment xmlns="ru.umc">
            <GUID>97fca397-c589-11e1-b4b7-3859f93b5c90</GUID>
            <AdditionalInformation>Дополнительная информация</AdditionalInformation>
            <Reason>Причина отмены заявки</Reason>
        </ru:CancelBookAnAppointment>
    </soap:Body>
</soap:Envelope>
```

```xml title="Тело ответа"
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
    <soap:Body>
        <m:CancelBookAnAppointmentResponse xmlns:m="ru.umc">
            <m:return xmlns:xs="http://www.w3.org/2001/XMLSchema"
                      xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"><?xml version="1.0"?>
                <РезультатВыполнения xmlns="S1" xmlns:xs="http://www.w3.org/2001/XMLSchema"
                                    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
                    <Результат>true</Результат>
                    <ОписаниеОшибки> </ОписаниеОшибки>
                </РезультатВыполнения>
            </m:return>
        </m:CancelBookAnAppointmentResponse>
    </soap:Body>
</soap:Envelope>
```