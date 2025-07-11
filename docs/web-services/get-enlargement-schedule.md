---
sidebar_position: 1
---

# GetEnlargementSchedule (укрупненное расписание)

## Описание

`GetEnlargementSchedule(StartDate[dateTime], FinishDate[dateTime])`

> Возвращает укрупненное расписание сотрудников, т.е. расписание без учета перерывов и занятого клиентами времени.
> Образуется посредством объединения самого раннего времени работы и самого позднего в один период (в разрезе дня).

## Возможные ошибки

1. Ошибка при преобразовании `StartDate` в дату;
2. Ошибка при преобразовании `FinishDate` в дату.

## Пример запроса

```xml title="Тело запроса"

<soap:Envelope xmlns:soap="http://www.w3.org/2003/05/soap-envelope" xmlns:ru="ru.umc">
    <soap:Header/>
    <soap:Body>
        <ru:GetEnlargementSchedule>
            <ru:StartDate>2017-03-01T00:00:00</ru:StartDate>
            <ru:FinishDate>2017-03-01T00:00:00</ru:FinishDate>
        </ru:GetEnlargementSchedule>
    </soap:Body>
</soap:Envelope>
```

```xml title="Тело ответа"

<soap:Envelope xmlns:soap="http://www.w3.org/2003/05/soap-envelope">
    <soap:Body>
        <m:GetEnlargementScheduleResponse xmlns:m="ru.umc">
            <m:return xmlns:xs="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
                <![CDATA[<?xml version="1.0"?>
                <ГрафикиДляСайта xmlns="S1" xmlns:xs="http://www.w3.org/2001/XMLSchema"
                                 xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
                    <ГрафикДляСайта>
                        <Клиника>f679444a-22b7-11df-8618-002618dcef2c</Клиника>
                        <СотрудникФИО>Ковалёва И.М.</СотрудникФИО>
                        <СотрудникID>6cf96534-3870-11e2-87ba-002618dcef2c</СотрудникID>
                        <Специализация>Офтальмология</Специализация>
                        <ПериодыГрафика>
                            <СвободноеВремя>
                                <ПериодГрафика>
                                    <Дата>2017-03-01T00:00:00</Дата>
                                    <ВремяНачала>2017-03-01T09:00:00</ВремяНачала>
                                    <ВремяОкончания>2017-03-01T20:00:00</ВремяОкончания>
                                </ПериодГрафика>
                            </СвободноеВремя>
                            <ЗанятоеВремя/>
                        </ПериодыГрафика>
                        <ДлительностьПриема>0001-01-01T00:15:00</ДлительностьПриема>
                    </ГрафикДляСайта>
                    <ГрафикДляСайта>
                        <Клиника>f679444a-22b7-11df-8618-002618dcef2c</Клиника>
                        <СотрудникФИО>Филатова М.С.</СотрудникФИО>
                        <СотрудникID>eab46ee6-94b1-11e3-87ec-002618dcef2c</СотрудникID>
                        <Специализация>Неврология</Специализация>
                        <ПериодыГрафика>
                            <СвободноеВремя>
                                <ПериодГрафика>
                                    <Дата>2017-03-01T00:00:00</Дата>
                                    <ВремяНачала>2017-03-01T09:00:00</ВремяНачала>
                                    <ВремяОкончания>2017-03-01T20:00:00</ВремяОкончания>
                                </ПериодГрафика>
                            </СвободноеВремя>
                            <ЗанятоеВремя/>
                        </ПериодыГрафика>
                        <ДлительностьПриема>0001-01-01T00:15:00</ДлительностьПриема>
                    </ГрафикДляСайта>
                </ГрафикиДляСайта>
                ]]>
            </m:return>
        </m:GetEnlargementScheduleResponse>
    </soap:Body>
</soap:Envelope>
```