---
sidebar_position: X
---

# ServiceName (краткое описание)

## Описание

```text
ServiceName(Parameter1[type], Parameter2[type], Params[Structure] ...)
```

`Parameter1` – короткое описание параметра.
`Parameter2` – короткое описание параметра.

### Параметры

| **Параметр** | **Тип** | **Описание** |
|--------------|---------|--------------|
| Parameter1   | string  | Описание     |
| Parameter2   | dateTime| Описание     |

> Подробное описание сервиса и его функциональности.

## Возможные ошибки

1. Описание первой возможной ошибки;
2. Описание второй возможной ошибки.

## Пример запроса

```xml title="Тело запроса"
<soap:Envelope xmlns:soap="http://www.w3.org/2003/05/soap-envelope" xmlns:ru="ru.umc">
    <soap:Header/>
    <soap:Body>
        <ru:ServiceName>
            <ru:Parameter1>value1</ru:Parameter1>
            <ru:Parameter2>value2</ru:Parameter2>
        </ru:ServiceName>
    </soap:Body>
</soap:Envelope>
```

```xml title="Тело ответа"
<soap:Envelope xmlns:soap="http://www.w3.org/2003/05/soap-envelope">
    <soap:Body>
        <m:ServiceNameResponse xmlns:m="ru.umc">
            <m:return>
                <!-- Response content -->
            </m:return>
        </m:ServiceNameResponse>
    </soap:Body>
</soap:Envelope>
```
