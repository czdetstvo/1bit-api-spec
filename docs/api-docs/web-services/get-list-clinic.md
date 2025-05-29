---
sidebar_position: 8
---

# GetListClinic (список филиалов)

## Описание

```text
GetListClinic()
```

> Возвращает список клиник с их уникальными идентификаторами.

## Пример запроса

```xml title="Тело запроса"
<soap:Envelope xmlns:soap="http://www.w3.org/2003/05/soap-envelope" xmlns:ru="ru.umc">
    <soap:Header/>
    <soap:Body>
        <ru:GetListClinic/>
    </soap:Body>
</soap:Envelope>
```

```xml title="Тело ответа"
<soap:Envelope xmlns:soap="http://www.w3.org/2003/05/soap-envelope">
    <soap:Body>
        <m:GetListClinicResponse xmlns:m="ru.umc">
            <m:return xmlns:xs="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"><![CDATA[<?xml version="1.0"?>
            <СписокКлиник xmlns="S1" xmlns:xs="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
                <Клиника>
                    <Наименование>Второй центр</Наименование>
                    <УИД>4c68deb4-22c3-11df-8618-002618dcef2c</УИД>
                </Клиника>
                <Клиника>
                    <Наименование>Третий центр</Наименование>
                    <УИД>66abf7b4-2ff9-11df-8625-002618dcef2c</УИД>
                </Клиника>
                <Клиника>
                    <Наименование>Центральная клиника</Наименование>
                    <УИД>f679444a-22b7-11df-8618-002618dcef2c</УИД>
                </Клиника>
            </СписокКлиник>]]></m:return>
        </m:GetListClinicResponse>
    </soap:Body>
</soap:Envelope>
```