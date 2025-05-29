---
sidebar_position: 4
---

# BookAnAppointmentWithParams (запись с сайта)

## Описание

```text
BookAnAppointmentWithParams(EmployeeID[string], PatientSurname[string], PatientName[string], PatientFatherName[string], Date[dateTime], TimeBegin[dateTime], Comment[string], Phone[string], Email[string], Address[string], Clinic[string], GUID[string], Params[Structure])
```

`Params` – структура с необязательными параметрами:

| **Параметр** | **Тип** | **Описание** |
|--------------|---------|--------------|
| **Birthday** | dateTime | Дата рождения клиента |
| **Duration** | dateTime | Длительность записи |
| **DurationType** | string | Метод расчета длительности заявки. Доступен один вариант значения: «ServiceDuration» – расчет длительности заявки из длительности услуг. Для расчета необходимо указать услуги в параметре Services |
| **Services** | string | Уникальные идентификаторы услуг в 1С, разделенные символом «;» (точка с запятой) |

> Производит запись клиента по уникальному идентификатору брони, который можно получить в следствие бронирования времени, с помощью «GetReserve».

### Правила расчета длительности записи:

1. При указанных параметрах DurationType и Services параметр Duration игнорируется, длительность рассчитывается из нормативов услуг;
2. При указанном параметре Duration – указанная длительность;
3. Если не задана параметрами – из основной длительности приема сотрудника;
4. Если и для сотрудника она не указана – базовая периодичность планирования по Учетной политике.

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

```xml title="Тело запроса"
<soap:Envelope xmlns:soap="http://www.w3.org/2003/05/soap-envelope" xmlns:ru="ru.umc" xmlns:core="http://v8.1c.ru/8.1/data/core">
    <soap:Header/>
    <soap:Body>
        <ru:BookAnAppointmentWithParams>
            <ru:EmployeeID>ac30e139-3087-11dc-8594-005056c00008</ru:EmployeeID>
            <ru:PatientSurname>Иванов</ru:PatientSurname>
            <ru:PatientName>Иван</ru:PatientName>
            <ru:PatientFatherName>Иванович</ru:PatientFatherName>
            <ru:Date>2017-03-17T00:00:00</ru:Date>
            <ru:TimeBegin>0001-01-01T13:10:00</ru:TimeBegin>
            <ru:Comment>Комментарий</ru:Comment>
            <ru:Phone>89876543210</ru:Phone>
            <ru:Email>bit@1cbit.ru</ru:Email>
            <ru:Address>Ленина 1</ru:Address>
            <ru:Clinic>f679444a-22b7-11df-8618-002618dcef2c</ru:Clinic>
            <ru:GUID>9cc6b9fc-0b04-11e7-b13c-00e051000230</ru:GUID>
            <ru:Params>
                <core:Property name="Birthday">
                    <core:Value>1980-09-14T00:00:00</core:Value>
                </core:Property>
                <core:Property name="Duration">
                    <core:Value>0001-01-01T01:30:00</core:Value>
                </core:Property>
                <core:Property name="DurationType">
                    <core:Value>ServiceDuration</core:Value>
                </core:Property>
                <core:Property name="Services">
                    <core:Value>eb20edcc-3ee0-11de-b0dd-0050bf5d92cb;8e045f06-da18-11e1-bab2-1803736d59cd</core:Value>
                </core:Property>
            </ru:Params>
        </ru:BookAnAppointmentWithParams>
    </soap:Body>
</soap:Envelope>
```

```xml title="Тело ответа"
<soap:Envelope xmlns:soap="http://www.w3.org/2003/05/soap-envelope">
    <soap:Body>
        <m:BookAnAppointmentWithParamsResponse xmlns:m="ru.umc">
            <m:return xmlns:xs="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"><![CDATA[<?xml version="1.0"?>
            <ОтветНаЗаписьССайта xmlns="S1" xmlns:xs="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
                <Результат>true</Результат>
                <ОписаниеОшибки> </ОписаниеОшибки>
            </ОтветНаЗаписьССайта>]]></m:return>
        </m:BookAnAppointmentWithParamsResponse>
    </soap:Body>
</soap:Envelope>
```