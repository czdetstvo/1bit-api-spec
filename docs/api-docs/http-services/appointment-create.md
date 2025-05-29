---
sidebar_position: 2
---

# AppointmentCreate (Создание заявки или листа ожидания)

**Стандартный шаблон URL (PATTERN\_URL):** /AppointmentCreate

**HTTP-Метод POST**. Создание или изменение в базе документа заявка или создание листа ожидания с переданными данными. Подробнее в описании параметра Method [ниже](#описание-параметра-method).

Является аналогом следующих веб-сервисов:
BookAnAppointment, BookAnAppointmentWithClient, FastBookAnAppointment, FastBookAnAppointmentWithClient, BookAnAppointmentWithParams.

## Параметры в теле запроса

|  |  |  |  |
| --- | --- | --- | --- |
| **Наименование** | **Обязательный** | **Тип значения** | **Описание** |
| Key | Да | string | Значение «Ключ API» для конкретной настройки обмена |
| Method | Да | string | Имя модели поведения сервиса. Может быть: BookAnAppointment, BookAnAppointmentWithClient, FastBookAnAppointment, FastBookAnAppointmentWithClient, BookAnAppointmentWithParams |
| Date | Да | dateTime | **Дата** на которую создаётся заявка/лист ожидания. Если указано вместе с временем - время игнорируется |
| TimeBegin | Да | dateTime | **Время** на которое создаётся заявка/лист ожидания. Если указано вместе с датой - дата игнорируется |
| Clinic | Да | string | УИД клиники расписания |
| EmployeeID | Да\* | string | УИД сотрудника к которому создаётся заявка  \* – Игнорируется FastBookAnAppointment и FastBookAnAppointmentWithClient |
| EquipmentCabinet | Нет | string | УИД оборудования, к которому оформляется заявка. Используется, когда нужно записать и сотрудника и кабинет/оборудования  Игнорируется FastBookAnAppointment и FastBookAnAppointmentWithClient |
| Client | Да\* | string | УИД клиента в базе для записи  \* – Обязательный для BookAnAppointmentWithClient и FastBookAnAppointmentWithClient |
| Service | Да\* | string | УИД или УИДы номенклатуры для записи  \* – Обязательный для метода BookAnAppointmentWithClient |
| GUID | Нет | string | УИД Заявки, которую надо изменить (вместо создания новой)  Игнорируется в FastBookAnAppointment и FastBookAnAppointmentWithClient |
| PatientSurname | Нет | string | Фамилия пациента  Игнорируется FastBookAnAppointmentWithClient и BookAnAppointmentWithClient |
| PatientName | Нет | string | Имя пациента  Игнорируется в FastBookAnAppointmentWithClient и BookAnAppointmentWithClient |
| PatientFatherName | Нет | string | Отчество пациента  Игнорируется в FastBookAnAppointmentWithClient и BookAnAppointmentWithClient |
| Comment | Нет | string | Комментарий к Заявке/Листу ожидания |
| Phone | Нет | string | Телефон пациента  Игнорируется в FastBookAnAppointmentWithClient и BookAnAppointmentWithClient |
| Email | Нет | string | Электронный адрес пациента  Игнорируется в FastBookAnAppointmentWithClient и BookAnAppointmentWithClient |
| Address | Нет | string | Адрес проживания пациента  Игнорируется в FastBookAnAppointmentWithClient и BookAnAppointmentWithClient |
| Specialization | Нет | string | Примечание о желаемой специализации в листе заявки.  Используется у FastBookAnAppointment |
| Birthday | Нет | dateTime | **Дата** рождения клиента. Если указано вместе с временем - время игнорируется  Используется у BookAnAppointmentWithParams |
| Duration | Нет | dateTime | Планируемая длительность заявки. Ожидается **время**. Если указано вместе с датой - дата игнорируется |
| DurationType | Нет | string | Способ расчёта длительности услуг заявки (Если параметр Duration пустой).  Может быть: «**ServiceDuration**» - Расчёт по стандартному времени услуг.  Если не указан или не тот, что описан выше, то предполагаемое время будет рассчитано из настроек стандартного приёма сотрудника и учётной политики |

## Описание параметра Method

Параметр «Method» обязателен. Если он не задан, то вернётся ошибка. Все варианты метода принимают как значение явное указание клиента (Client). Если клиент явно не указан, то некоторые методы могут его искать и создать, если клиент не был найден. Поиск осуществляется согласно настройкам обмена с сайтом, если они не указаны, то клиент будет создаваться каждый раз.

Все методы принимают параметр ожидаемой длительности (Duration), если он не был задан, то проверяется параметр DurationType, в котором можно явно указать вид поиска по номенклатуре. Если номенклатуры нет или параметр задан иначе, то расчёт времени проводится согласно стандартному приёму у сотрудника или настройкам учётной политики.

Методы работы с заявками (BookAnAppointment, BookAnAppointmentWithClient и BookAnAppointmentWithParams) являются схожими и различаются нагрузкой на систему. Аналогично и с методами по созданию листов ожидания (FastBookAnAppointment и FastBookAnAppointmentWithClient).

Параметр «Method» определяет поведение обработки:

**BookAnAppointment** – Создание или изменение Заявки (Изменение если был передан параметр GUID). Создаёт заявку на конкретного сотрудника. Может искать клиента, если тот явно не задан.

**BookAnAppointmentWithClient** – Создание или изменение Заявки (Изменение если был передан параметр GUID). Создаёт заявку на конкретного сотрудника. Требуется передавать перечень услуг для заявки.

**FastBookAnAppointment** – Создание Листа ожидания. Может искать клиента, если тот явно не задан. Позволяет указать желаемую специализацию.

**FastBookAnAppointmentWithClient** – Создание Листа ожидания. Позволяет передавать перечень услуг для листа ожидания.

**BookAnAppointmentWithParams** – Создание или изменение Заявки (Изменение если был передан параметр GUID). Создаёт заявку на конкретного сотрудника. Может искать клиента, если тот явно не задан. Позволяет передавать перечень услуг для заявки.

## Примеры

### Создание заявки (BookAnAppointment)

Создадим заявку длительностью 40 минут. Укажем имя, фамилию и телефон клиента. Настройка обмена с сайтом задана так, что первый критерий поиска - это Фамилия и Имя, второй критерий - телефонный номер.

Тело запроса JSON:

```json
{
  "Key": "1111aaaa2222bbbb3333cccc4444dddd",
  "Method": "BookAnAppointment",
  "EmployeeID": "e7005e6d-65c9-11e9-936d-1856809fe650",
  "Clinic": "f679444a-22b7-11df-8618-002618dcef2c",
  "TimeBegin": "9:10:00",
  "Date": "20.10.2024",
  "PatientName": "Борис",
  "PatientSurname": "Бубаков",
  "Phone": "8-800-555-35-35",
  "Duration": "0:40:00"
}
```

Возвращаемый результат:

Тело ответа:

```json
{
  "Ответ": {
    "Результат": "true",
    "ОписаниеОшибки": "",
    "УИД": "55b17f33-8abe-11ef-9542-08979885f491"
  }
}
```

### Изменение заявки (BookAnAppointmentWithClient)

Изменим созданную ранее заявку - передадим в качестве параметра GUID, что был возвращён в предыдущем примере. Добавим кабинет, перенесём время и добавим список услуг из двух элементов. При изменении заявки в теле ответа будет возвращён тот же самый УИД, что и был передан. В этом методе необходимо явно указать клиента.

Тело запроса JSON:

```json
{
  "Key": "1111aaaa2222bbbb3333cccc4444dddd",
  "Method": "BookAnAppointmentWithClient",
  "EmployeeID": "e7005e6d-65c9-11e9-936d-1856809fe650",
  "Clinic": "f679444a-22b7-11df-8618-002618dcef2c",
  "GUID": "55b17f33-8abe-11ef-9542-08979885f491",
  "TimeBegin": "14:00:00",
  "Date": "18.10.2024",
  "Client": "92c7ea9d-2cab-11e4-9f84-1078d2d69bb4",
  "EquipmentCabinet": "5210c9c3-65a2-11e9-936d-1856809fe650",
  "Service": "222df5d1-4964-11e9-82be-40167e631f2e; 9fa37e64-4952-11e9-82be-40167e631f2e"
}
```

Возвращаемый результат:

Тело ответа:

```json
{
  "Ответ": {
    "Результат": "true",
    "ОписаниеОшибки": "",
    "УИД": "55b17f33-8abe-11ef-9542-08979885f491"
  }
}
```

### Изменение заявки (BookAnAppointmentWithParams)

Т.к. в прошлом примере не был указан DurationType, и Duration, то время посчиталось по стандартному времени указанного сотрудника. При изменении заявки, номенклатура и кабинет изменяются согласно переданным параметрам. Поэтому мы уберём из заявки кабинет, не указывая его в теле запроса. Пересчитаем время относительно переданных номенклатур и сменим клиента.

Тело запроса JSON:

```json
{
  "Key": "1111aaaa2222bbbb3333cccc4444dddd",
  "Method": "BookAnAppointmentWithParams",
  "EmployeeID": "e7005e6d-65c9-11e9-936d-1856809fe650",
  "Clinic": "f679444a-22b7-11df-8618-002618dcef2c",
  "GUID": "55b17f33-8abe-11ef-9542-08979885f491",
  "TimeBegin": "14:00:00",
  "Date": "18.10.2024",
  "PatientName": "Борис",
  "PatientSurname": "Бубаков",
  "Phone": "8-800-555-35-35",
  "Service": "222df5d1-4964-11e9-82be-40167e631f2e; 9fa37e64-4952-11e9-82be-40167e631f2e",
  "DurationType": "ServiceDuration"
}
```