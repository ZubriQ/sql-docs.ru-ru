---
title: Каталог базы данных WideWorldImporters | Документы Microsoft
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: ''
ms.component: samples
ms.technology:
- samples
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e47c0022-ce87-4ba5-a24b-df55efe66431
caps.latest.revision: 3
author: BarbKess
ms.author: barbkess
manager: craigg
robots: noindex,nofollow
ms.workload: On Demand
ms.openlocfilehash: 0d458bc15530aa87bfa922787558fff3f07645f7
ms.sourcegitcommit: 094c46e7fa6de44735ed0040c65a40ec3d951b75
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/07/2018
---
# <a name="wideworldimporters-database-catalog"></a>Каталог базы данных WideWorldImporters
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
База данных WideWorldImporters содержит все сведения о транзакциях и ежедневных данных для продажи и покупки, а также данные датчика для автомобилей и холодные комнаты.

## <a name="schemas"></a>Схемы

WideWorldImporters использует схемы для различных целей, таких как хранение данных, определение способа доступа к данным для пользователей и предоставление объектов для интеграции и разработки баз данных хранилища.

### <a name="data-schemas"></a>Данные схемы

Эти схемы содержат данные. Количество таблиц требуются все схемы и расположены в схеме приложения.

|Схема|Описание|
|-----------------------------|---------------------|
|Приложение|Приложения. Пользователи, контакты и параметры. Это также содержит ссылочные таблицы с данными, используется несколько схем|
|Purchasing|Элемент склада покупок от поставщиков и сведения о поставщиках.|  
|Продажи|Биржевая элемента продажи, розничные клиенты и сведения о клиентах и продажах людей. |  
|Warehouse|Элемент склада инвентаризации и транзакции.|  

### <a name="secure-access-schemas"></a>Схемы безопасного доступа

Эти схемы используются для внешних приложений, которые не разрешены для прямого доступа к таблицам данных. Они содержат, представлений и хранимых процедур, используемых внешними приложениями.

|Схема|Описание|
|-----------------------------|---------------------|
|Веб-сайт|Весь доступ к базе данных с веб-сайта компании выполняется с помощью этой схемы.|
|Отчеты|Весь доступ к базе данных из отчетов служб Reporting Services выполняется с помощью этой схемы.|
|PowerBI|Весь доступ к базе данных из панели мониторинга Power BI через корпоративный шлюз выполняется с помощью этой схемы.|

Обратите внимание, что отчеты и PowerBI схемы не используются в первоначальной версии образца базы данных. Тем не менее все службы Reporting Services и Power BI образцы, построенных на основе этой базы данных рекомендуется использовать эти схемы.

### <a name="development-schemas"></a>Разработка схемы

Специальная схемы

|Схема|Описание|
|-----------------------------|---------------------|
|Интеграция|Объекты и действия, необходимые для интеграции хранилища данных (т. е. Перемещение данных в базу данных WideWorldImportersDW).|
|Последовательности;|Содержит последовательности, используемый всеми таблицами в приложении.|

## <a name="tables"></a>Таблицы

Все таблицы в базе данных — в схем данных.

### <a name="application-schema"></a>Схема приложения

Подробные сведения о параметрах и людей (пользователи и контакты), а также общие таблицы ссылок (общие для нескольких схем).

|Таблица|Описание|
|-----------------------------|---------------------|
|SystemParameters|Содержит настраиваемые параметры для всей системы.|
|Пользователи|Содержит имя пользователя, контактные данные для всех, кто использовать приложение, а также для людей, посвящена Wide World Importers в организации клиента. Сюда входят сотрудников, клиентов, поставщиков и других контактов. Пользователям, которым предоставлены разрешения на использование системы или веб-сайта информация включает сведения об имени входа.|
|Городов|Существует много адресов, которые хранятся в системе, для людей, адреса доставки для клиентов организации, раскладки адресов во поставщики и т. д. Всякий раз, когда хранится адрес, является ссылкой на Город в этой таблице. Имеется также пространственного местоположения для каждого города.|
|StateProvinces|Города являются частью штатов или провинций. Эта таблица содержит подробные сведения о них, включая Пространственные данные, описывающие границ каждого штата или провинции.|
|Страны|Являются частью стран, штатов или провинций. Эта таблица содержит подробные сведения о них, включая Пространственные данные, описывающие границы каждой страны.|
|DeliveryMethods|Варианты доставка стандартных элементов (например, грузовик или фургон, post, отправки, courier, и т. д.)|
|PaymentMethods|Варианты для выполнения платежей (например, денежных средств, проверка электронных ПЛАТЕЖЕЙ, и т. д.)|
|TransactionTypes|Типы заказчика, поставщика или биржевые операции (например, счета, кредит примечание, и т. д.)|

### <a name="purchasing-schema"></a>Приобретение схемы

Данные поставщики и покупок элемент склада.

|Таблица|Описание|
|-----------------------------|---------------------|
|Suppliers|Основной сущности таблицы для поставщиков (организаций)|
|SupplierCategories|Категории для поставщиков (например, novelties, toys, одежда, упаковки и т. д.)|
|SupplierTransactions|Все финансовые транзакции, связанные с поставщиком (счета, платежи)|
|PurchaseOrders|Подробные сведения заказов на покупку поставщика|
|PurchaseOrderLines|Заказы на покупку строки подробных данных от поставщика|

 
### <a name="sales-schema"></a>Продажи схемы

Сведения клиентов, менеджеров по продажам и продаж запасов товаров.

|Таблица|Описание|
|-----------------------------|---------------------|
|Измерение заказчиков|Основной сущности таблицы для клиентов (организаций или пользователей)|
|CustomerCategories|Категории для клиентов (ie нестандартные хранилищ, супермаркетах, и т. д.)|
|BuyingGroups|Организаций-клиентов может быть частью группы, которые точный степень приобретения|
|CustomerTransactions|Всех финансовых операций, связанных с клиентами (счета, платежи)|
|SpecialDeals|Специальные цены. Это может включать фиксированной цены, скидки в долларах или процент скидки.|
|Orders|Подробные сведения о заказах клиентов|
|OrderLines|Строки подробных данных из клиентских заказов|
|Счета|Подробные сведения о накладных клиента|
|InvoiceLines|Строки подробных данных из накладных клиента|

### <a name="warehouse-schema"></a>Схема хранилища

Сведения о стандартных элементов, их активах и транзакции.

|Таблица|Описание|
|-----------------------------|---------------------|
|StockItems|Таблица основной сущности для хранения элементов|
|StockItemHoldings|Без временных столбцы для хранения элементов. Это часто обновляемые столбцы.|
|StockGroups|Группы для классификация стандартных элементов (например, novelties, toys, пищевые novelties, и т. д.)|
|StockItemStockGroups|Стандартных элементов, на который stock групп (многие ко многим)|
|Цвета|Стандартных элементов (при необходимости) может иметь цветов|
|PackageTypes|Можно упаковать на складе способы (например, поле, упаковке, палитра, кг, и т. д.|
|StockItemTransactions|Транзакции, охватывающие все перемещения всех стандартных элементов (прием, продажи, списания)|
|VehicleTemperatures|Регулярно записанные температуры chillers автомобиля|
|ColdRoomTemperatures|Регулярно записываются температуру chillers холодного комнаты|


## <a name="design-considerations"></a>Вопросы проектирования

Субъективная структуры базы данных и нет возможности или неточности созданию базы данных. Показать идеи о том, как можно разработать собственную базу данных, схемы и таблицы в этой базе данных.

### <a name="schema-design"></a>Структура схемы

WideWorldImporters использует несколько схем, который позволяет легко понять системы базы данных и демонстрируют принципы базы данных.  

Во всех возможных случаях база данных collocates таблицы, которые часто запрашиваются вместе в той же схеме, чтобы свести к минимуму сложности соединения.

Схема базы данных была в код создан на основе ряда таблицы метаданных в другой базе данных WWI_Preparation. Это дает WideWorldImporters очень высокой степенью согласованности проектирования, именования согласованность и полноты. Подробные сведения о том, как была создана схема исходного кода: [расширенных world-importers/wwi скриптов базы данных](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/wide-world-importers/sample-scripts)

### <a name="table-design"></a>Конструктор таблиц

- Все таблицы имеют один столбец первичного ключа для простоты соединения.
- Все схемы, таблицы, столбцы, индексы и проверочные ограничения имеют описание расширенное свойство, которое можно использовать для определения назначения объект или столбец. Оптимизированные для памяти таблицы являются исключением это так, как они не поддерживают в настоящее время расширенные свойства.
- Все внешние ключи автоматически индексируются, если нет другого некластеризованный индекс, имеющий один и тот же компонент слева.
- Автоматическая нумерация таблиц основан на последовательности. Эти последовательности легче работать с всех связанных серверов и похожих средах от столбцов ИДЕНТИФИКАТОРОВ. Оптимизированные для памяти таблицы использования столбцов ИДЕНТИФИКАТОРОВ, поскольку они не поддерживают в SQL Server 2016.
- Одну последовательность (TransactionID) используется для этих таблиц: CustomerTransactions, SupplierTransactions и StockItemTransactions. Этот пример демонстрирует, как набор таблиц, может иметь одну последовательность.
- Некоторые столбцы имеют соответствующие значения по умолчанию.

### <a name="security-schemas"></a>Схемы безопасности

Для безопасности WideWorldImporters не разрешать внешние приложения прямой доступ к схем данных. Чтобы изолировать доступ, WideWorldImporters использует схемы доступа, которые не содержат данных, но содержит представления и хранимые процедуры. Внешние приложения для извлечения данных, они могут просматривать использовать схемы безопасности.  Таким образом, пользователи могут запускать только представлений и хранимых процедур в схемах безопасного доступа

Например этот пример включает панели мониторинга Power BI. Внешнее приложение обращается к эти панели мониторинга Power BI из шлюза Power BI как пользователь, имеющий разрешение только для чтения в схеме PowerBI.  Для разрешения только для чтения пользователь должен только разрешения SELECT и EXECUTE на схему, PowerBI. Администратор баз данных на WWI назначает эти разрешения, при необходимости.

## <a name="stored-procedures"></a>Хранимые процедуры

Хранимые процедуры, упорядочены в схемах. Большая часть схемы используются для целей образец или конфигурации.

`Website` Схема содержит хранимые процедуры, которые могут использоваться веб-интерфейса.

`Reports` И `PowerBI` схемы предназначены для служб reporting services и целях PowerBI. Любые расширения образца рекомендуется использовать эти схемы для целей отчетности.

### <a name="website-schema"></a>Схема веб-сайта

Это процедуры, используемые клиентским приложением, например веб-интерфейса.

|Процедура|Назначение|
|-----------------------------|---------------------|
|ActivateWebsiteLogon|Позволяет пользователю (из `Application.People`) должна иметь доступ к веб-сайту.|
|Изменение пароля|Изменяет пароль пользователя (для пользователей, которые не используются механизмы внешней проверки подлинности).|
|InsertCustomerOrders|Позволяет Вставка (включая порядок строк) одного или нескольких заказов клиента.|
|InvoiceCustomerOrders|Принимает список для выставления счетов и обрабатывает счетов.|
|RecordColdRoomTemperatures|Принимает список данных датчика, в качестве возвращающего табличное значение параметр и применяет данные к `Warehouse.ColdRoomTemperatures` временная таблица.|
|RecordVehicleTemperature|Принимает массив JSON и использует его для обновления `Warehouse.VehicleTemperatures`.|
|SearchForCustomers|Поиск клиентов по имени или части имени (название организации или имя пользователя).|
|SearchForPeople|Выполняет поиск людей по имени или части имени.|
|SearchForStockItems|Выполняет поиск стандартных элементов по имени или части имени или маркетинговые комментарии.|
|SearchForStockItemsByTags|Выполняет поиск стандартных элементов по тегам.|
|SearchForSuppliers|Поиск поставщиков по имени или части имени (название организации или имя пользователя).|

### <a name="integration-schema"></a>Интеграция схемы

В процессе ETL используются хранимые процедуры в этой схеме. Они получают данные, необходимые из различных таблиц, за период, предусмотренного [ETL-пакета](etl-workflow.md).

### <a name="dataloadsimulation-schema"></a>DataLoadSimulation схемы

Имитирует рабочей нагрузки, которая вставляет продажи и покупки. Главная хранимая процедура — `PopulateDataToCurrentDate`, который используется для вставки образец данных до текущей даты.

|Процедура|Назначение|
|-----------------------------|---------------------|
|Configuration_ApplyDataLoadSimulationProcedures|Воссоздает процедуры необходимых данных моделирование нагрузки. Это необходимо для переноса данных до текущей даты.|
|Configuration_RemoveDataLoadSimulationProcedures|Эта функция удаляет процедуры снова после завершения моделирования данных.|
|DeactiveTemporalTablesBeforeDataLoad|Удаляет temporal характер всех временных таблиц и там, где это применимо, применяется триггер, чтобы можно внести изменения, как будто они применялись на более раннюю, чем разрешено sys темпоральные таблицы.|
|PopulateDataToCurrentDate|Используется для переноса данных до текущей даты. Должны быть выполнены перед параметры конфигурации после восстановления базы данных из первоначального резервного копирования.|
|ReactivateTemporalTablesAfterDataLoad|Вновь устанавливает темпоральных таблиц, включая проверку согласованности данных. (Удаление триггеров).|


### <a name="application-schema"></a>Схема приложения

Эти процедуры используются для настройки образца. Они используются для применения функции выпуска enterprise до версии выпуска standard edition образца, а также добавлять аудит и полнотекстового индексирования.

|Процедура|Назначение|
|-----------------------------|---------------------|
|AddRoleMemberIfNonexistant|Добавляет члена в роль, если элемент еще не в роли|
|Configuration_ApplyAuditing|Добавляет аудита. Аудит сервера применяется для баз данных standard edition; Аудит дополнительные базы данных добавляется для выпуска enterprise edition.|
|Configuration_ApplyColumnstoreIndexing|Применяет индексирование columnstore `Sales.OrderLines` и `Sales.InvoiceLines` и reindexes соответствующим образом.|
|Configuration_ApplyFullTextIndexing|Применяет полнотекстовых индексов для `Application.People`, `Sales.Customers`, `Purchasing.Suppliers`, и `Warehouse.StockItems`. Заменяет `Website.SearchForPeople`, `Website.SearchForSuppliers`, `Website.SearchForCustomers`, `Website.SearchForStockItems`, `Website.SearchForStockItemsByTags` с замены процедур, которые используют полнотекстовое индексирование.|
|Configuration_ApplyPartitioning|Применяется для секционирования таблиц `Sales.CustomerTransactions and `Purchasing.SupplierTransactions и изменяет порядок индексов в соответствии с.|
|Configuration_ApplyRowLevelSecurity|Применяет безопасность на уровне строк для фильтрации заказчиков по продажам территории, связанные с ролями.|
|Configuration_ConfigureForEnterpriseEdition|Применяет columnstore индексирования, полный текст, в памяти, polybase и секционирование.|
|Configuration_EnableInMemory|Добавляет файловую группу оптимизированной для памяти (если не работает в Azure), заменяет `Warehouse.ColdRoomTemperatures`, `Warehouse.VehicleTemperatures` на эквиваленты в памяти и переносит данные, повторно создает `Website.OrderIDList`, `Website.OrderList`, `Website.OrderLineList`, `Website.SensorDataList` табличных типов на эквиваленты, оптимизированных для памяти, удаляет и воссоздает процедуры `Website.InvoiceCustomerOrders`, `Website.InsertCustomerOrders`, и `Website.RecordColdRoomTemperatures` , использующий эти табличные типы.|
|Configuration_RemoveAuditing|Удаляет конфигурацию аудита.|
|Configuration_RemoveRowLevelSecurity|Удаляет конфигурацию безопасности на уровне строк (это необходимо для изменения в связанных таблицах).|
|CreateRoleIfNonExistant|Создает роль базы данных, если он еще не существует.|


### <a name="sequences-schema"></a>Схемы последовательностей

Процедуры для настройки последовательностей в базе данных.

|Процедура|Назначение|
|-----------------------------|---------------------|
|ReseedAllSequences|Вызывает процедуру ReseedSequenceBeyondTableValue для всех последовательностей.|
|ReseedSequenceBeyondTableValue|Используется для изменения положения следующего значения из последовательности за значение в таблице, которая использует ту же последовательность. (Например, DBCC CHECKIDENT для идентификации столбцов эквивалент для последовательностей, но потенциально нескольким таблицам).|