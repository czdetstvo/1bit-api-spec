# FastBookAnAppointment (создать лист ожидания)

**FastBookAnAppointment** (Specialization[string], PatientSurname[string], PatientName[string],
PatientFatherName[string], Date[dateTime], TimeBegin[dateTime], Comment[string], Phone[string], Email[string],
Address[string], Clinic[string]).

**Clinic** – уникальный идентификатор клиники.

Описание: Создает лист ожидания записи в 1с.

Возможные ошибки:

1. Ошибка при преобразовании Date в дату;
2. Ошибка при преобразовании TimeBegin в Дату;
3. Ошибка при поиске клиники по переданному наименованию;
4. Не удалось записать документ ЛистОжидания.

## Пример запроса:

```xml title="Тело запроса"

<soap:Envelope xmlns:soap="http://www.w3.org/2003/05/soap-envelope" xmlns:ru="ru.umc">
    <soap:Header/>
    <soap:Body>
        <ru:FastBookAnAppointment>
            <ru:Specialization>Хирургия</ru:Specialization>
            <ru:PatientSurname>Иванов</ru:PatientSurname>
            <ru:PatientName>Иван</ru:PatientName>
            <ru:PatientFatherName>Иванович</ru:PatientFatherName>
            <ru:Date>2017-03-17T00:00:00</ru:Date>
            <ru:TimeBegin>0001-01-01T14:00:00</ru:TimeBegin>
            <ru:Comment>Или в 16:00</ru:Comment>
            <ru:Phone>89876543210</ru:Phone>
            <ru:Email>bit@1cbit.ru</ru:Email>
            <ru:Address>Ул. Ленина 1</ru:Address>
            <ru:Clinic>f679444a-22b7-11df-8618-002618dcef2c</ru:Clinic>
        </ru:FastBookAnAppointment>
    </soap:Body>
</soap:Envelope>
```

```xml title="Пример ответа"

<soap:Envelope xmlns:soap="http://www.w3.org/2003/05/soap-envelope">
    <soap:Body>
        <m:FastBookAnAppointmentResponse xmlns:m="ru.umc">
            <m:return xmlns:xs="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
                <![CDATA[<?xml version="1.0"?>
                <ОтветНаЗаписьССайта xmlns="S1" xmlns:xs="http://www.w3.org/2001/XMLSchema"
                                     xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
                    <Результат>true</Результат>
                    <ОписаниеОшибки></ОписаниеОшибки>
                </ОтветНаЗаписьССайта>
                ]]></m:return>
        </m:FastBookAnAppointmentResponse>
    </soap:Body>
</soap:Envelope>
```