---
title: Термины глоссария ADO | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- ADO, glossary
ms.assetid: b0478836-4123-4357-969a-c5784fc28be5
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4b92f9c8b65db459d46aff51b7aed58c3ff6e307
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "76940435"
---
# <a name="ado-glossary-terms"></a>Термины глоссария ADO
В этом разделе определяются термины, относящиеся к ADO.

## <a name="a"></a>Объект
 абсолютный URL-адрес полный URL-адрес, указывающий расположение ресурса, расположенного в Интернете или интрасети. См. также *URL-адрес* и *ОТНОСИТЕЛЬНЫЙ URL-адрес*.

 Элемент управления ActiveX с собственной регистрацией, внутрипроцессный COM-компонент, который часто имеет визуальный элемент во время разработки или выполнения. Элементы управления ActiveX также могут взаимодействовать с активным контейнером документа, таким как Microsoft Internet Explorer.

 АДИСАПИ (расширенный интерфейс прикладного программного интерфейса Интернет-сервера данных) DLL ISAPI, которая обеспечивает синтаксический анализ, управление автоматизацией, маршалирование набора записей и упаковку MIME. Компонент АДИСАПИ работает через API, предоставляемый службы IIS (IIS). См. также *ISAPI*.

 Агрегатная функция в запросе, функция, например COUNT, AVG или STDEV, которая вычисляет значение с помощью всех строк в столбце таблицы. При написании выражений и программировании можно использовать агрегатные функции SQL (включая три перечисленные выше) и агрегатные функции предметной области для определения различных статистических показателей.

 псевдоним альтернативное имя, присваиваемое столбцу или выражению в инструкции SQL SELECT, которое часто короче или более информативно. Например, Бобсалес является псевдонимом в следующей инструкции SELECT: "выберите WR-Sales как Бобсалес from SalesDB". Псевдоним можно использовать для динамического назначения столбцов для управления привязками в объекте элемента управления.

 апартаментная потоковая цепочка потоковой модели COM, в которой все вызовы объекта происходят в одном потоке. В потоковом апартаменте COM-вызовы синхронизируются и маршалируются. См. также *коммддефком*.

 асинхронная операция, которая возвращает управление вызывающей программе, не дожидаясь завершения операции. До завершения операции выполнение кода продолжится. См. также *синхронные операции*.

## <a name="b"></a>B
 Привязка записи сопоставление поля в таблице и переменной. В расширениях ADO Visual C++ поля **набора записей** сопоставляются с переменными C/C++.

 Битовая маска числовое значение, предназначенное для сравнения побитовых значений с другими числовыми значениями, обычно для отметки параметров в параметрах или возвращаемых значениях. Обычно это сравнение выполняется с помощью побитовых логических операторов, таких как **and** и **or** в **&** Visual Basic и **&#124;** в C++.

 Например, значения ADO **фиелдаттрибутинум** можно использовать в качестве битовых масок для определения атрибутов поля. Предположим, необходимо определить, было ли поле обновляемым. Это можно проверить с помощью следующего выражения в Visual Basic:`Field.Attributes AND adFldUpdatable`

 Если результат имеет значение TRUE, поле доступно для обновления.

 Закладка маркера, который однозначно определяет строку в наборе строк, чтобы пользователь мог быстро переходить к нему.

 бизнес-объект. объект, выполняющий определенный набор операций, например проверку данных или логику бизнес-правил. Бизнес-объекты обычно находятся на среднем уровне.

 Бизнес-правило. сочетание изменений проверки, проверки входа, поиска в базе данных, политик и алгоритмных преобразований, которые составляют корпоративный способ ведения бизнеса. Также называется *бизнес-логикой*.

## <a name="c"></a>C
 Вычисляемое выражение выражение, которое не является константой, но его значение зависит от других значений. Для вычисления вычисляемое выражение должно получать и считывать значения из других источников, обычно в других полях или строках.

 Глава — ссылка на диапазон строк из источника данных. В ADO глава обычно является ссылкой на другой **набор записей**.

 Столбцы раздела позволяют определить связь типа « *родители-потомки* », в *которой родительским объектом* является **набор записей** , содержащий столбец «Chapter», а *дочерний* элемент — **набор записей** , представленный главой.

 раздел — псевдоним псевдонима, ссылающийся на столбец, добавленный к родительскому элементу.

 Задает сопоставление набора символов с их числовыми значениями. Например, Юникод — это 16-разрядная кодировка, способная кодировать все известные символы и использоваться в качестве стандарта кодировки символов мира.

 Дочерняя сторона зависимой стороны иерархической связи. Дочерний элемент — это узел в иерархической структуре, имеющий другой узел (ближе к корню). См *. также*отношение *дочерний псевдоним*, *родитель-потомок*.

 дочерний псевдоним псевдонима, который ссылается на дочерний элемент. См. также *псевдоним*, *дочерний элемент*.

 CLSID (идентификатор класса) универсальный уникальный идентификатор (UUID), определяющий COM-компонент. Каждый COM-компонент имеет свой идентификатор CLSID в реестре Windows, чтобы его можно было загрузить из других приложений. См. также *ProgID*, *com*.

 уровень клиента — логический уровень распределенной системы, который обычно представляет данные и обрабатывает ввод пользователя, иногда называемый *внешним*интерфейсом. Как правило, клиентский уровень запрашивает данные с сервера на основе входных данных, а затем форматирует и отображает результат. См. также *средний уровень*, *уровень источника данных*, *распределенное приложение*.

 COM (объектная модель компонента) — двоичный стандарт, который позволяет объектам взаимодействовать в сетевой среде независимо от языка, на котором они были разработаны или на каких компьютерах они находятся. Технологии на основе COM включают элементы управления ActiveX, автоматизацию и связывание и внедрение объектов (OLE). COM позволяет объекту предоставлять свои функциональные возможности другим компонентам и размещать приложения. Он определяет, как объект предоставляет себя и как эта экспозиция работает между процессами и между сетями. COM также определяет жизненный цикл объекта.

 Двоичный файл компонента COM, такой как DLL, OCX и некоторые exe-файлы, поддерживающий стандарт COM для предоставления объектов. Такой файл содержит код для одной или нескольких фабрик классов, COM-классов, механизмов записи реестра, загрузки кода и т. д.

 оператор сравнения оператор, который сравнивает два выражения и возвращает логическое значение.

 Параметр критерия, который может быть выражен как ">" (больше), "\<" (меньше), "=" (равно), ">=" (больше или равно), "<=" (меньше или равно), "<>" (не равно) или "Like" (сопоставление шаблонов).

 компонент содержит объект, инкапсулирующий как данные, так и код, а также предоставляет хорошо указанный набор общедоступных служб.

 составной файл реализация структурированного хранилища COM для файлов. Составной файл хранит отдельные объекты в одном структурированном файле, состоящем из двух основных элементов: объектов хранилища и объектов потока. Вместе они работают как файловая система в файле.

 Несколько отдельных файлов, связанных в одном физическом файле. Доступ к каждому отдельному файлу в составном файле можно получить, как если бы он был одним физическим файлом.

 постоянное значение числового или строкового значения, которое не изменяется. Именованные перечисления ADO (перечислимые константы) можно использовать в коде вместо фактических значений, например **адусеклиент** — это константа, значение которой равно 3. (Const Адусеклиент = 3). См. также *перечисление*.

 курсор элемента базы данных, управляющего навигацией по записям, обновлением данных и видимостью изменений, внесенных в базу данных другими пользователями.

## <a name="d"></a>D
 Привязка данных процесс связывания объектов или элементов управления приложения с источником данных. Элемент управления, связанный с источником данных, называется *элементом управления с привязкой к данным*.

 Содержимое элемента управления с привязкой к данным связано со значениями из базы данных. Например, элемент управления Grid, привязанный к объекту **Recordset** , может обновляться при обновлении строк в **наборе записей** . Когда **набор записей**извлекает новые значения, в сетке отображаются новые значения.

 Программное обеспечение поставщика данных, которое предоставляет доступ к данным приложению ADO либо напрямую, либо через поставщика услуг. См. также поставщик служб.

 формирование данных — это методика, которая использует формальный синтаксис (называемый **языком фигур**) для определения специализированного объекта **Recordset** (который называется *набором записей в форме формы*), который содержит не только данные, но и ссылки на другие объекты **наборов записей** и (или) вычисленные значения на основе этих объектов **Recordset** .

 уровень источника данных — логический уровень распределенной системы, представляющий компьютер, на котором работает СУБД, например база данных SQL Server. См. также: *уровень клиента*, *средний уровень*, *распределенное приложение*.

 Протокол DCOM, который позволяет COM-компонентам взаимодействовать напрямую друг с другом по сети. См. также *com*, *Component*.

 DDL (язык описания данных) — это инструкции в SQL, которые определяют, а не управляют данными. Схема базы данных создается или изменяется с помощью DDL. Например, в инструкциях SQL DDL **создаются** **CREATE TABLE**, **Grant**и **REVOKE** .

 поток по умолчанию текстовый или двоичный поток (представленный объектом **потока** ), связанный с объектами **записи** или **Recordset** при использовании определенных поставщиков OLE DB, таких как поставщик Microsoft OLE DB для публикации в Интернете. Поток по умолчанию обычно содержит содержимое файла, например код HTML для корня веб-сайта.

 распределенное приложение написано таким образом, что обработка может быть распределена между несколькими компьютерами по сети. Как правило, распределенное приложение делится на представления, бизнес-логику и уровни хранилища данных или *уровни*. См. также уровень клиента, промежуточный уровень, уровень источника данных.

 Отключенный набор записей объект **набора записей** в кэше клиента, который больше не имеет активного подключения к серверу. Если исходный источник данных должен быть снова доступен по какой-либо причине, например для обновления данных, соединение должно быть установлено заново. Однако доступ к коллекциям, свойствам и методам в отключенном **наборе записей** по-прежнему возможен.

 DML (язык обработки данных) — это инструкции в SQL, которые управляют, а не определяют данные. Значения в базе данных выбираются и изменяются с помощью DML. Например, инструкции SQL DML могут быть инструкциями **вставки**, **обновления**, **удаления**и **выбора** .

 Поставщик источника документов — особый класс поставщиков, управляющих папками и документами. Если документ представлен объектом **записи** или папка документов представляется объектом **Recordset** , то поставщик источника документа заполняет эти объекты уникальным набором полей, описывающих характеристики документа, а не сам документ. См. также запись ресурса.

 DSN (имя источника данных) коллекция сведений, используемых для подключения приложения к определенной базе данных ODBC. Диспетчер драйверов ODBC использует эти сведения для создания подключения к базе данных. ИМЯ DSN может храниться в файле (Файловый DSN) или в реестре Windows (DSN компьютера).

 динамическое свойство свойство, относящееся к поставщику данных или службе курсора. Коллекция **свойств** объекта заполняется автоматически (динамически). Объект не имеет динамических свойств до тех пор, пока он не будет подключен к источнику данных с помощью определенного поставщика данных. См. также: поставщик данных, курсор.

## <a name="e"></a>E
 Перечисление списка именованных констант. Перечисляемые значения не должны быть уникальными. Однако имя каждого значения должно быть уникальным в пределах области, где определено перечисление. В ADO перечисления используются для числовых параметров и возвращаемых значений, для добавления смысла в код ADO и для защиты разработчика от числовых значений (которые могут меняться от версии к версии). Например, чтобы открыть статический **набор записей**, используйте перечислимое значение **адопенстатик** :`Recordset.Open ,,adOpenStatic`

 Также называется *константой с перечислением*. См. также *константа*.

 событие, распознаваемое объектом, для которого можно написать код для ответа. События могут создаваться с помощью выполнения команд, завершения транзакций, навигации по набору записей и обновлений данных, помимо других действий. См. также *обработчик событий*.

 обработчик событий — это код, который выполняется при возникновении события. См. также событие.

## <a name="h"></a>H
 обработчик — это подпрограммы, управляющие общим и относительно простым условием или операцией, например восстановлением ошибок или управлением данными.

 иерархический набор **записей, который содержит** другой **набор записей**. См. также формирование данных, глава.

 Дополнительные сведения см. [в разделе доступ к строкам в иерархическом наборе записей](../ado/guide/data/accessing-rows-in-a-hierarchical-recordset.md).

 Иерархия в целом иерархия — это упорядоченная структура с верхним и подчиненными уровнями. В ADO иерархические **наборы записей** используются для представления связи «родители-потомки» между записью и главой. Кроме того, в ADO объекты **записи** и **потока** можно использовать для доступа к иерархическим древовидным структурам, таким как папка и документы. Объекты данных ActiveX (MD) также содержит объекты **иерархии** для представления связи между уровнями измерения в кубе OLAP. См. также иерархические наборы записей, связь «родители-потомки», глава, дерево.

## <a name="i-l"></a>I-L
 ISAPI (интерфейс прикладного программирования Интернет-сервера) — набор функций для Интернет-серверов, таких как Windows NT® Server или Windows 2000 Server под управлением Microsoft® службы IIS (IIS).

 Key столбец или столбцы в таблице, однозначно идентифицирующие строку. часто используется для индексирования таблицы.

## <a name="m"></a>M
 Маршалирование процесса упаковки, отправки и распаковки параметров метода интерфейса через границы потока или процесса.

 Средний уровень логический слой в распределенной системе между пользовательским интерфейсом, веб-клиентом и базой данных. Обычно это место, где создаются экземпляры бизнес-объектов. Средний уровень — это набор бизнес-правил и функций, которые создают и работают над получением информации. Это достигается с помощью бизнес-правил, которые могут часто изменяться и инкапсулироваться в компоненты, физически отделенные от самой логики приложения. Также известен как *уровень сервера приложений*. См. также: распределенное приложение, клиентский уровень, уровень источника данных.

 MIME (многоцелевое расширение электронной почты Интернета), изначально разработанный Интернет-протокол, позволяющий обмениваться сообщениями электронной почты с богатым содержимым в разнородных сетях, компьютерах и средах электронной почты. На практике MIME также был принят и расширен приложениями, не являющимися почтой.

 Стандарт MIME позволяет публиковать и читать двоичные данные в Интернете. Заголовок файла с двоичными данными содержит тип MIME данных; Это информирует клиентские программы (например, веб-браузеры и почтовые пакеты) о том, что им нужно будет выполнять обработку данных иначе, чем при обработке непосредственного текста. Например, заголовок веб-документа, содержащего рисунок JPEG, содержит тип MIME, относящийся к формату файла JPEG. Это позволяет браузеру отображать файл с помощью средства просмотра JPEG, если оно имеется.

## <a name="n-o"></a>N-O
 узел элемент в иерархической древовидной структуре. Узел может быть корнем или дочерним узлом другого узла. Узел также может быть родительским для нескольких дочерних элементов. См. также иерархия, дерево, корень, дочерний элемент.

 переменная объекта переменная, содержащая ссылку на объект. Например, `objCustomObject` переменная, указывающая на объект типа кустомобжект:`Set objCustomObject = CreateObject(adodb.Recordset)`

 ODBC (открытие подключения к базе данных) — Стандартный интерфейс языка программирования, используемый для подключения к различным источникам данных. Обычно доступ к нему осуществляется через панель управления, где имена источников данных (DSN) могут быть назначены для использования конкретных драйверов ODBC.

 OLE DB набор интерфейсов, которые предоставляют доступ к данным из различных источников с помощью COM. OLE DB интерфейсы предоставляют приложения с единообразным доступом к данным, хранящимся в различных источниках информации. Эти интерфейсы поддерживают функцию СУБД, соответствующую источнику данных, что позволяет ему совместно использовать свои данные. См. также COM.

 Оптимистическая блокировка тип блокировки, в которой страница данных, содержащая одну или несколько записей, включая редактируемую запись, недоступна для других пользователей, только пока запись обновляется методом **Update** , но доступна до и после вызова **Update**.

 Оптимистическая блокировка используется при открытии объекта **Recordset** с параметром или свойством **LockType** , имеющим значение **adLockOptimistic** или **адлоккбатчоптимистик**. См. также Пессимистическая блокировка.

 Порядковое значение числовое расположение элемента в порядке. В коллекции ADO порядковое значение первого элемента равно нулю (0). Следующий элемент — один (1) и т. д.

## <a name="p"></a>P
 Параметризованная команда. запрос или команда, позволяющие задать значения параметров перед выполнением команды. Например, строка SQL может быть параметризована путем встраивания маркеров параметров в строку SQL (обозначенную символом "?"). Затем приложение задает значения для каждого параметра и выполняет команду.

 родительский элемент управления для иерархической связи. В иерархической структуре родительский узел имеет один или несколько дочерних узлов, расположенных непосредственно под ним в иерархии. См. также связь «родители-потомки», дочерняя.

 родительский псевдоним псевдоним, который ссылается на родительский элемент. См. также псевдоним, родительский элемент.

 связь «родители-потомки» — это отношение в иерархической структуре, в которой родительский элемент находится на одном уровне выше и напрямую связан с одним или несколькими дочерними элементами. Дочерний элемент находится на одном уровне ниже и должен иметь один родительский элемент. См. также родительский, дочерний элемент.

 Пессимистическая блокировка. тип блокировки, в которой страница, содержащая одну или несколько записей, включая редактируемую запись, недоступна другим пользователям для обеспечения обновления. Поведение пессимистической блокировки определяется поставщиком OLE DB. Как правило, записи блокируются при редактировании и остаются недоступными до завершения метода **Update** .

 Пессимистическая блокировка включается при открытии объекта **Recordset** с параметром или свойством **LockType** , имеющим значение **адлоккпессимистик**. См. также Оптимистическая блокировка.

 объединение оптимизации производительности на основе использования коллекций предварительно выделенных ресурсов, таких как объекты или подключения к базам данных. Более эффективно нарисовать существующий ресурс из пула, чем создавать новый ресурс.

 ProgID (программный идентификатор) уникальное имя, сопоставленное с реестром Windows приложением COM. ProgID для подключения ADO — "ADODB. Соединение ". См. также CLSID, COM.

 прокси объект, зависящий от интерфейса, обеспечивающий упаковку и связь параметров, необходимые клиенту для вызова объекта приложения, выполняющегося в другой среде выполнения, например в другом потоке или в другом процессе. Прокси-сервер размещается вместе с клиентом и взаимодействует с соответствующей заглушкой, расположенной с вызываемым объектом приложения. См. также заглушку.

## <a name="r"></a>R
 относительный URL-адрес частично квалифицированный URL-адрес, указывающий ресурс в Интернете или интрасети, расположение которого отсчитывается относительно начальной точки, указанной абсолютным URL-адресом или эквивалентным объектом соединения ADO. По сути, Объединенные абсолютные и относительные URL-адреса конситуте полный URL-адрес. См. также URL-адрес и абсолютный URL-адрес.

 удаленный источник данных источник данных, который существует на другом компьютере, а не в локальной системе (где выполняется клиентское приложение).

 запись ресурса A из поставщика источника документа, который содержит поля для определения и описания папки или документа. Сам документ не содержится в записи ресурса, но обычно к нему можно получить доступ по потоку по умолчанию или по полю в записи ресурса, содержащей URL-адрес. См. также: поставщик источника документа, поток по умолчанию, URL-адрес.

 набора строк набор строк из источника данных с одинаковой схемой полей. Набор строк может представлять все или некоторые поля из таблицы. Набор строк может также представлять виртуальную таблицу, созданную запросом или соединением двух или более таблиц. В ADO наборы строк представлены объектами **Recordset** .

## <a name="s"></a>S
 Область действия диапазона ссылок для объекта или переменной или диапазона записей в представлении или таблице. Например, на локальные переменные можно ссылаться только внутри процедуры, в которой они были определены. Общедоступные переменные доступны из любого места в приложении. Объекты, такие как текущая база данных, находятся в области, если они находятся в определенном пути поиска. Диапазоны записей можно указать с помощью предложения Scope во многих командах.

 Программное обеспечение поставщика услуг, которое инкапсулирует службу, создавая и используя данные, расширяя возможности в приложениях ADO. Это поставщик, который не предоставляет данные напрямую, вместо того, чтобы предоставлять службу, например обработку запросов. Поставщик услуг может обрабатывать данные, предоставленные поставщиком данных. См. также поставщик данных.

 Набор записей в форме набора **записей** , столбцы которых были специально определены и содержат не только данные, но также ссылки (называемые главами) на другие объекты **набора записей** и (или) вычисленные значения на основе других объектов **Recordset** .

 родственный элемент любого из двух или более узлов в иерархической структуре, находящиеся на одном уровне иерархии. Корневой узел в иерархии не имеет одноуровневых элементов.

 хранимая процедура предкомпилированная коллекция кода, такая как инструкции SQL и необязательные инструкции управления потоком, которые хранятся под именем и обрабатываются как единое целое. Хранимые процедуры хранятся в базе данных; они могут выполняться с одним вызовом из приложения и разрешать объявляемые пользователем переменные, условное выполнение и другие мощные функции программирования.

 Заглушка объектно-определяемого интерфейса, обеспечивающего упаковку и связь параметров, необходимых объекту приложения для получения вызовов от клиента, выполняющегося в другой среде выполнения, например в другом потоке или в другом процессе. Заглушка находится в объекте приложения и взаимодействует с соответствующим прокси-сервером, который расположен с клиентом, который его вызывает. См. также: proxy.

 подчиненный узел см. в разделе дочерний элемент.

 синхронная операция. операция, инициированная кодом, который завершается до запуска следующей операции. См. также асинхронные операции.

## <a name="t-z"></a>T-Z
 Дерево представляет структуру, представляющую иерархическую связь между элементами (узлами). На верхнем уровне дерева (корень) имеется один узел. Под корнем может быть несколько дочерних элементов. Все дочерние элементы могут, в свою очередь, являться родительскими для других дочерних элементов, таким образом, ветвление подобно дереву. Типичным примером древовидной структуры является папка, содержащая документы и другие папки. См. также иерархия, узел, корень, дочерний элемент.

 Веб-сервер — компьютер, предоставляющий веб-службы и страницы пользователям интрасети и Интернета.
