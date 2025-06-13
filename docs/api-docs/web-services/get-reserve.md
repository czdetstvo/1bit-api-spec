---
sidebar_position: 4
---

# GetReserve (бронь времени на оформление записи с сайта)

## Описание

```text
GetReserve(Specialization[string], Date[dateTime], TimeBegin[dateTime], EmployeeID[string], Clinic[string])
```

### Параметры

| **Параметр**   | **Тип**  | **Описание**                        |
|----------------|----------|-------------------------------------|
| Specialization | string   | Специализация врача                 |
| Date           | dateTime | Дата, на которую оформляется бронь  |
| TimeBegin      | dateTime | Время начала брони                  |
| EmployeeID     | string   | Уникальный идентификатор сотрудника |
| Clinic         | string   | Уникальный идентификатор клиники    |

> Производит резервирование времени, возвращает уникальный идентификатор заявки, который необходимо использовать в
> «BookAnAppointment», в качестве значения GUID.

## Возможные ошибки

1. Ошибка при получении уникального идентификатора на основе EmployeeID;
2. Ошибка при выполнении поиска сотрудника по уникальному идентификатору;
3. Ошибка при преобразовании Date в дату;
4. Ошибка при преобразовании TimeBegin в Дату;
5. Ошибка при расчете времени окончания: в базе не настроена периодичность бронирования и у сотрудника не задана
   длительность приема;
6. Ошибка при расчете времени окончания;
7. Ошибка при поиске клиники по переданному наименованию;
8. Не удалось записать документ Заявка.

## Пример запроса

```xml title="Тело запроса"

<soap:Envelope xmlns:soap="http://www.w3.org/2003/05/soap-envelope" xmlns:ru="ru.umc">
    <soap:Header/>
    <soap:Body>
        <ru:GetReserve>
            <ru:Specialization>Неврология</ru:Specialization>
            <ru:Date>2017-03-17T00:00:00</ru:Date>
            <ru:TimeBegin>0001-01-01T15:00:00</ru:TimeBegin>
            <ru:EmployeeID>ac30e139-3087-11dc-8594-005056c00008</ru:EmployeeID>
            <ru:Clinic>f679444a-22b7-11df-8618-002618dcef2c</ru:Clinic>
        </ru:GetReserve>
    </soap:Body>
</soap:Envelope>
```

## Пример ответа

```xml title="Тело ответа"

<soap:Envelope xmlns:soap="http://www.w3.org/2003/05/soap-envelope">
    <soap:Body>
        <m:GetReserveResponse xmlns:m="ru.umc">
            <m:return xmlns:xs="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
                <![CDATA[<?xml version="1.0"?>
<ОтветНаЗаписьССайта xmlns="S1" xmlns:xs="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
<Результат>true</Результат>
<ОписаниеОшибки> </ОписаниеОшибки>
<УИД>9cc6b9fc-0b04-11e7-b13c-00e051000230</УИД>
</ОтветНаЗаписьССайта>]]></m:return>
        </m:GetReserveResponse>
    </soap:Body>
</soap:Envelope>
```
