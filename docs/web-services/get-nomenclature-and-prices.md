---
sidebar_position: 9
---

# GetNomenclatureAndPrices (прайс-лист)

## Описание

```text
GetNomenclatureAndPrices(GUID[string], Params[string])
```

`GUID` – уникальный идентификатор клиники.

`Params` – не используется в дальнейшем.

> Получает список номенклатуры, соответствующий отбору, а также основных услуг сотрудников и цен на них для выбранного филиала по выбранному прейскуранту.

Внимание, для работы данного пункта необходимо создать настройку обмена с сайтом на необходимый филиал и указать прайс! (Вкладка «Администрирование» – «Настройки обмена с сайтом»).

## Возможные ошибки

1. Ошибка при получении уникального идентификатора на основе GUID;
2. Ошибка при выполнении поиска клиники по уникальному идентификатору;
3. Не удалось получить настройку обмена (приходит ответ аналогичный неудачной записи документа Заявка).

## Пример запроса

```xml title="Тело запроса"
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
    <soap:Body>
        <ru:GetNomenclatureAndPrices xmlns="ru.umc">
            <Clinic>4c68deb4-22c3-11df-8618-002618dcef2c</Clinic>
            <Params>
                <!-- Optional -->
                <Property xmlns="http://v8.1c.ru/8.1/data/core">
                    <Value></Value>
                </Property>
            </Params>
        </ru:GetNomenclatureAndPrices>
    </soap:Body>
</soap:Envelope>
```

```xml title="Тело ответа"
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
    <soap:Body>
        <m:GetNomenclatureAndPricesResponse xmlns:m="ru.umc">
            <m:return xmlns:xs="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"><![CDATA[<?xml version="1.0"?>
            <Каталоги xmlns="S2" xmlns:xs="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
                <Каталог>
                    <UID xsi:type="xs:string">b468afaa-f720-11e5-8273-40167e631f2e</UID>
                    <Наименование>Прочие услуги</Наименование>
                    <Артикул/>
                    <БазоваяЕдиницаИзмерения/>
                    <Цена>0</Цена>
                    <Продолжительность>0001-01-01T00:15:00</Продолжительность>
                    <Вид/>
                    <Родитель>00000000-0000-0000-0000-000000000000</Родитель>
                    <ЭтоПапка>true</ЭтоПапка>
                </Каталог>
                <Каталог>
                    <UID xsi:type="xs:string">b468afac-f720-11e5-8273-40167e631f2e</UID>
                    <Наименование>Пребывание в стационаре, сутки, обычная палата</Наименование>
                    <Артикул/>
                    <БазоваяЕдиницаИзмерения/>
                    <Цена>890</Цена>
                    <Продолжительность>0001-01-01T00:15:00</Продолжительность>
                    <Вид>Услуга</Вид>
                    <Родитель>b468afaa-f720-11e5-8273-40167e631f2e</Родитель>
                    <ЭтоПапка>false</ЭтоПапка>
                </Каталог>
            </Каталоги>]]></m:return>
        </m:GetNomenclatureAndPricesResponse>
    </soap:Body>
</soap:Envelope>
```