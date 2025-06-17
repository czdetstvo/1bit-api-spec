---
sidebar_position: 7
---

# GetListEmployees (список сотрудников)

## Описание

```text
GetListEmployees()
```

> Возвращает список сотрудников с их уникальными идентификаторами.

## Пример запроса

```xml title="Тело запроса"
<soap:Envelope xmlns:soap="http://www.w3.org/2003/05/soap-envelope" xmlns:ru="ru.umc">
    <soap:Header/>
    <soap:Body>
        <ru:GetListEmployees/>
    </soap:Body>
</soap:Envelope>
```

```xml title="Тело ответа"
<soap:Envelope xmlns:soap="http://www.w3.org/2003/05/soap-envelope">
    <soap:Body>
        <m:GetListEmployeesResponse xmlns:m="ru.umc">
            <m:return xmlns:xs="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"><![CDATA[<?xml version="1.0"?>
            <Сотрудники xmlns="S2" xmlns:xs="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
                <Сотрудник>
                    <UID xsi:type="xs:string">eab46ee6-94b1-11e3-87ec-002618dcef2c</UID>
                    <Наименование>Филатова Мария Сергеевна</Наименование>
                    <Фамилия>Филатова</Фамилия>
                    <Имя>Мария</Имя>
                    <Отчество>Сергеевна</Отчество>
                    <Специализация>Офтальмология</Специализация>
                    <Организация>f679444a-22b7-11df-8618-002618dcef2c</Организация>
                    <ОсновныеУслуги/>
                    <СреднийРейтинг>4,0</СреднийРейтинг>
                    <КраткоеОписание/>
                </Сотрудник>
                <Сотрудник>
                    <UID xsi:type="xs:string">9e8b672a-9975-11e3-87ec-002618dcef2c</UID>
                    <Наименование>Скрипко Юлия Александровна</Наименование>
                    <Фамилия>Скрипко</Фамилия>
                    <Имя>Юлия</Имя>
                    <Отчество>Александровна</Отчество>
                    <Специализация>Офтальмология</Специализация>
                    <Организация>f679444a-22b7-11df-8618-002618dcef2c</Организация>
                    <ОсновныеУслуги/>
                    <СреднийРейтинг>4,0</СреднийРейтинг>
                    <КраткоеОписание/>
                </Сотрудник>
            </Сотрудники>]]></m:return>
        </m:GetListEmployeesResponse>
    </soap:Body>
</soap:Envelope>
```