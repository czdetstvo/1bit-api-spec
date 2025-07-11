---
sidebar_position: 5
---

# BookAnAppointment (запись с сайта)

**BookAnAppointment** (EmployeeID[string], PatientSurname[string], PatientName[string], PatientFatherName[string], Date[dateTime], TimeBegin[dateTime], Comment[string], Phone[string], Email[string], Address[string], Clinic[string], GUID[string]).

**EmployeeID** – уникальный идентификатор сотрудника.

**Clinic** – уникальный идентификатор клиники.

Описание: Производит запись клиента по уникальному идентификатору брони, который можно получить в следствие бронирования времени, с помощью «GetReserve».

## Возможные ошибки

1. Ошибка при получении уникального идентификатора на основе EmployeeID;
2. Ошибка при выполнении поиска сотрудника по уникальному идентификатору;
3. Ошибка при преобразовании Date в дату;
4. Ошибка при преобразовании TimeBegin в Дату;
5. Ошибка при расчете времени окончания: в базе не настроена периодичность бронирования и у сотрудника не задана длительность приема;
6. Ошибка при расчете времени окончания;
7. Ошибка при поиске клиники по переданному наименованию;
8. Не удалось записать документ Заявка.

## Пример запроса

```xml
<soap:Envelope xmlns:soap="http://www.w3.org/2003/05/soap-envelope" xmlns:ru="ru.umc">
  <soap:Header/>
  <soap:Body>
    <ru:BookAnAppointment>
      <ru:EmployeeID>ac30e139-3087-11dc-8594-005056c00008</ru:EmployeeID>
      <ru:PatientSurname>Иванов</ru:PatientSurname>
      <ru:PatientName>Иван</ru:PatientName>
      <ru:PatientFatherName>Иванович</ru:PatientFatherName>
      <ru:Date>2017-03-17T00:00:00</ru:Date>
      <ru:TimeBegin>0001-01-01T15:00:00</ru:TimeBegin>
      <ru:Comment>Запись с сайта</ru:Comment>
      <ru:Phone>+7 (999) 999-99-99</ru:Phone>
      <ru:Email>test@test.ru</ru:Email>
      <ru:Address>г. Москва, ул. Тестовая, д. 1</ru:Address>
      <ru:Clinic>f679444a-22b7-11df-8618-002618dcef2c</ru:Clinic>
      <ru:GUID>9cc6b9fc-0b04-11e7-b13c-00e051000230</ru:GUID>
    </ru:BookAnAppointment>
  </soap:Body>
</soap:Envelope>
```

## Пример ответа

```xml
<soap:Envelope xmlns:soap="http://www.w3.org/2003/05/soap-envelope">
  <soap:Body>
    <m:BookAnAppointmentResponse xmlns:m="ru.umc">
      <m:return xmlns:xs="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"><![CDATA[<?xml version="1.0"?>
<ОтветНаЗаписьССайта xmlns="S1" xmlns:xs="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
<Результат>true</Результат>
<ОписаниеОшибки> </ОписаниеОшибки>
<УИД>9cc6b9fc-0b04-11e7-b13c-00e051000230</УИД>
</ОтветНаЗаписьССайта>]]></m:return>
    </m:BookAnAppointmentResponse>
  </soap:Body>
</soap:Envelope>
```