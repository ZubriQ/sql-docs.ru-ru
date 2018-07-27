---
title: Наборы строк и курсоры SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB rowsets, cursors
- SQL Server Native Client OLE DB provider, rowsets
- rowsets [OLE DB], cursors
- properties [OLE DB]
- cursors [OLE DB]
ms.assetid: 26a11e26-2a3a-451e-8f78-fba51e330ecb
caps.latest.revision: 30
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d7c1768beb903e214260c2b6a37486bfc2583c0c
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37416364"
---
# <a name="rowsets-and-sql-server-cursors"></a>Наборы строк и курсоры SQL Server
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращает результирующие наборы пользователям двумя способами.  
  
-   Результирующие наборы по умолчанию, которые характеризуются следующим:  
  
    -   Сводят издержки к минимуму.  
  
    -   Обеспечивают максимальную производительность при выборке данных.  
  
    -   Поддерживают лишь функции однопроходных курсоров только для чтения.  
  
    -   Возвращают пользователю по одной строке одновременно.  
  
    -   Поддерживают одновременно только одну активную инструкцию в каждом соединении.  
  
         После выполнения инструкции другие инструкции можно будет выполнить в этом соединении только после извлечения пользователем всех результатов или отмены этой инструкции.  
  
    -   Поддерживают все инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
-   Серверные курсоры, которые характеризуются следующим:  
  
    -   Поддерживают все функции курсоров.  
  
    -   Могут возвращать пользователю блоки строк.  
  
    -   Поддерживают несколько активных инструкций в одном соединении.  
  
    -   Позволяют выбирать наиболее применимые функциональные средства курсора с точки зрения производительности.  
  
         Поддержка функциональных средств курсора может привести к снижению производительности по отношению к результирующему набору по умолчанию. Это снижение производительности можно скомпенсировать, если пользователь имеет возможность применять функциональные средства курсоров для извлечения набора строк меньшего размера.  
  
    -   Не поддерживают инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)], которые возвращают несколько результирующих наборов.  
  
 Пользователь может запросить другой режим работы курсоров, установив определенные свойства набора строк. Если пользователь не задает ни одного из этих свойств набора строк или указывает для всех их значения по умолчанию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB для собственного клиента реализует набор строк при помощи результирующий набор по умолчанию. Если любое из этих свойств присвоено значение, отличное от по умолчанию, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB для собственного клиента реализует набор строк при помощи серверного курсора.  
  
 Следующие свойства набора строк служат для поставщика OLE DB собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] указанием использовать курсоры [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Некоторые свойства можно безопасно сочетать с другими. Например, набор строк, предоставляющий доступ к свойствам DBPROP_IRowsetScroll и DBPROP_IRowsetChange, становится набором строк с закладками, обеспечивающим возможность немедленного обновления. Другие свойства являются взаимоисключающими. Например, набор строк со свойством DBPROP_OTHERINSERT не может содержать закладок.  
  
|Идентификатор свойства|Значение|Поведение набора строк|  
|-----------------|-----------|---------------------|  
|DBPROP_SERVERCURSOR|VARIANT_TRUE|Обновление данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] через набор строк невозможно. Этот набор строк является последовательным и поддерживает только прямую прокрутку и выборку. Относительное позиционирование строки поддерживается. Текст команды может содержать предложение ORDER BY.|  
|DBPROP_CANSCROLLBACKWARDS или DBPROP_CANFETCHBACKWARDS|VARIANT_TRUE|Обновление данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] через набор строк невозможно. Этот набор строк поддерживает прокрутку и выборку в любом направлении. Относительное позиционирование строки поддерживается. Текст команды может содержать предложение ORDER BY.|  
|DBPROP_BOOKMARKS или DBPROP_LITERALBOOKMARKS|VARIANT_TRUE|Обновление данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] через набор строк невозможно. Этот набор строк является последовательным и поддерживает только прямую прокрутку и выборку. Относительное позиционирование строки поддерживается. Текст команды может содержать предложение ORDER BY.|  
|DBPROP_OWNUPDATEDELETE, DBPROP_OWNINSERT или DBPROP_OTHERUPDATEDELETE|VARIANT_TRUE|Обновление данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] через набор строк невозможно. Этот набор строк поддерживает прокрутку и выборку в любом направлении. Относительное позиционирование строки поддерживается. Текст команды может содержать предложение ORDER BY.|  
|DBPROP_OTHERINSERT|VARIANT_TRUE|Обновление данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] через набор строк невозможно. Этот набор строк поддерживает прокрутку и выборку в любом направлении. Относительное позиционирование строки поддерживается. Текст команды может включать предложение ORDER BY, если для указанных в ссылке столбцов существует индекс.<br /><br /> Если набор строк содержит закладки, свойство DBPROP_OTHERINSERT не может иметь значение VARIANT_TRUE. При попытке создать набор строк с этим свойством видимости и закладками возникает ошибка.|  
|DBPROP_IRowsetLocate или DBPROP_IRowsetScroll|VARIANT_TRUE|Обновление данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] через набор строк невозможно. Этот набор строк поддерживает прокрутку и выборку в любом направлении. Закладки и абсолютное позиционирование при помощи **IRowsetLocate** интерфейс поддерживаются в наборе строк. Текст команды может содержать предложение ORDER BY.<br /><br /> Свойства DBPROP_IRowsetLocate и DBPROP_IRowsetScroll требуют наличия закладок в наборе строк. При попытке создать набор строк с закладками и свойством DBPROP_OTHERINSERT, которому присвоено значение VARIANT_TRUE, возникает ошибка.|  
|DBPROP_IRowsetChange или DBPROP_IRowsetUpdate|VARIANT_TRUE|Возможно обновление данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] через набор строк. Этот набор строк является последовательным и поддерживает только прямую прокрутку и выборку. Относительное позиционирование строки поддерживается. Все команды, поддерживающие обновляемые курсоры, могут поддерживать эти интерфейсы.|  
|DBPROP_IRowsetLocate или DBPROP_IRowsetScroll и DBPROP_IRowsetChange или DBPROP_IRowsetUpdate|VARIANT_TRUE|Возможно обновление данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] через набор строк. Этот набор строк поддерживает прокрутку и выборку в любом направлении. Закладки и абсолютное позиционирование при помощи **IRowsetLocate** поддерживаются в наборе строк. Текст команды может содержать предложение ORDER BY.|  
|DBPROP_IMMOBILEROWS|VARIANT_FALSE|Обновление данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] через набор строк невозможно. Этот набор строк поддерживает только прямую прокрутку. Относительное позиционирование строки поддерживается. Текст команды может включать предложение ORDER BY, если для указанных в ссылке столбцов существует индекс.<br /><br /> Свойство DBPROP_IMMOBILEROWS можно использовать только в наборах строк, которые способны показывать в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] строки, вставленные командами в рамках других сеансов или другими пользователями. При попытке открыть набор строк с этим свойством, заданным равным VARIANT_FALSE, для любого набора строк, для которого свойство DBPROP_OTHERINSERT не может иметь значение VARIANT_TRUE, возникает ошибка.|  
|DBPROP_REMOVEDELETED|VARIANT_TRUE|Обновление данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] через набор строк невозможно. Этот набор строк поддерживает только прямую прокрутку. Относительное позиционирование строки поддерживается. Текст команды может содержать предложение ORDER BY, если это не запрещено другим свойством.|  
  
 Объект [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживаемый серверный курсор набора строк поставщика OLE DB для собственного клиента можно легко создать на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базовой таблицы или представления с помощью **IOpenRowset::OpenRowset** метод. Указывается имя таблицы или представления, передавая требуется набор строк задается *rgPropertySets* параметра.  
  
 Если пользователь требует, чтобы набор строк поддерживался серверным курсором, то возможности выбора текста команды, которая создает набор строк, становятся ограниченными. В частности, текст команды ограничивается применением либо одной инструкции SELECT, которая возвращает один результирующий набор строк, либо хранимой процедуры, реализующей одну инструкцию SELECT, которая возвращает результат в виде одного набора строк.  
  
 В двух этих таблицах показаны сопоставления различных свойств OLE DB и моделей курсоров. В них также показано, какие свойства набора строк следует задать, чтобы использовать модель курсора определенного типа.  
  
 В каждой ячейке таблицы содержится значение свойства набора строк для определенной модели курсора. Типы данных всех свойств наборов строк, приведенных выше в этом разделе, относятся к типу данных VT_BOOL, а их значением по умолчанию является VARIANT_FALSE. В таблице используются следующие символы:  
  
 F = значение по умолчанию (VARIANT_FALSE)  
  
 T = VARIANT_TRUE  
  
 \- = VARIANT_TRUE или VARIANT_FALSE  
  
 Чтобы ввести в действие модель курсора определенного типа, определите столбец, соответствующий этой модели курсора, и найдите все свойства набора строк со значением «Т» в этом столбце. Чтобы воспользоваться данной конкретной моделью курсора, присвойте этим свойствам набора строк значение VARIANT_TRUE. Свойствам набора строк, для которых в качестве значения указано «-», можно присваивать либо значение VARIANT_TRUE, либо значение VARIANT_FALSE.  
  
|Свойства набора строк и модели курсора|По умолчанию<br /><br /> набор по<br /><br /> набора<br /><br /> (RO)|быстрый;<br /><br /> однопроходный<br /><br /> только<br /><br /> (RO)|Статические<br /><br /> (RO)|Keyset<br /><br /> управляемый<br /><br /> (RO)|  
|--------------------------------------|-------------------------------------------|--------------------------------------------|-----------------------|----------------------------------|  
|DBPROP_SERVERCURSOR|Ж|T|T|T|  
|DBPROP_DEFERRED|Ж|Ж|-|-|  
|DBPROP_IrowsetChange|Ж|Ж|Ж|Ж|  
|DBPROP_IrowsetLocate|Ж|Ж|-|-|  
|DBPROP_IrowsetScroll|Ж|Ж|-|-|  
|DBPROP_IrowsetUpdate|Ж|Ж|Ж|Ж|  
|DBPROP_BOOKMARKS|Ж|Ж|-|-|  
|DBPROP_CANFETCHBACKWARDS|Ж|Ж|-|-|  
|DBPROP_CANSRCOLLBACKWARDS|Ж|Ж|-|-|  
|DBPROP_CANHOLDROWS|Ж|Ж|-|-|  
|DBPROP_LITERALBOOKMARKS|Ж|Ж|-|-|  
|DBPROP_OTHERINSERT|Ж|T|Ж|Ж|  
|DBPROP_OTHERUPDATEDELETE|Ж|T|Ж|T|  
|DBPROP_OWNINSERT|Ж|T|Ж|T|  
|DBPROP_OWNUPDATEDELETE|Ж|T|Ж|T|  
|DBPROP_QUICKSTART|Ж|Ж|-|-|  
|DBPROP_REMOVEDELETED|Ж|Ж|Ж|-|  
|DBPROP_IrowsetResynch|Ж|Ж|Ж|-|  
|DBPROP_CHANGEINSERTEDROWS|Ж|Ж|Ж|Ж|  
|DBPROP_SERVERDATAONINSERT|Ж|Ж|Ж|-|  
|DBPROP_UNIQUEROWS|-|Ж|Ж|Ж|  
|DBPROP_IMMOBILEROWS|-|-|-|T|  
  
|Свойства набора строк и модели курсора|Динамический (только для чтения)|С набором ключей (для чтения и записи)|Динамический (для чтения и записи)|  
|--------------------------------------|--------------------|---------------------|----------------------|  
|DBPROP_SERVERCURSOR|T|T|T|  
|DBPROP_DEFERRED|-|-|-|  
|DBPROP_IrowsetChange|Ж|-|-|  
|DBPROP_IrowsetLocate|Ж|-|Ж|  
|DBPROP_IrowsetScroll|Ж|-|Ж|  
|DBPROP_IrowsetUpdate|Ж|-|-|  
|DBPROP_BOOKMARKS|Ж|-|Ж|  
|DBPROP_CANFETCHBACKWARDS|-|-|-|  
|DBPROP_CANSRCOLLBACKWARDS|-|-|-|  
|DBPROP_CANHOLDROWS|Ж|-|Ж|  
|DBPROP_LITERALBOOKMARKS|Ж|-|Ж|  
|DBPROP_OTHERINSERT|T|Ж|T|  
|DBPROP_OTHERUPDATEDELETE|T|T|T|  
|DBPROP_OWNINSERT|T|T|T|  
|DBPROP_OWNUPDATEDELETE|T|T|T|  
|DBPROP_QUICKSTART|-|-|-|  
|DBPROP_REMOVEDELETED|T|-|T|  
|DBPROP_IrowsetResynch|-|-|-|  
|DBPROP_CHANGEINSERTEDROWS|Ж|-|Ж|  
|DBPROP_SERVERDATAONINSERT|Ж|-|Ж|  
|DBPROP_UNIQUEROWS|Ж|Ж|Ж|  
|DBPROP_IMMOBILEROWS|Ж|T|Ж|  
  
 Выбор модели курсора для конкретного ряда свойств набора строк определяется следующим образом.  
  
 Получите подмножество свойств, приведенных в предыдущих таблицах, из указанной коллекции свойств набора строк. В зависимости от значения флага для каждого свойства набора строк разделите эти свойства на две подгруппы — обязательные (T, F) и необязательные (-). Применительно к каждой модели курсора начните с первой таблицы и переходите слева направо, сравнивая значения свойств в этих двух подгруппах со значениями соответствующих свойств в этом столбце. Выбирается та модель курсора, для которой все обязательные свойства совпадают, а число несовпадений в необязательных свойствах минимально. При наличии нескольких моделей курсора выбирается самая левая.  
  
## <a name="sql-server-cursor-block-size"></a>Размер блока курсора SQL Server  
 Когда [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] курсор поддерживает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] набор строк поставщика OLE DB для собственного клиента, количество элементов в строке обработки параметра массива из **IRowset::GetNextRows** или **IRowsetLocate::GetRowsAt**  методы определяет размер блока курсора. Строки, указанные дескрипторами в массиве, являются элементами блока курсора.  
  
 Для наборов строк, которые поддерживают закладки, дескрипторов строк извлекается с помощью **IRowsetLocate::GetRowsByBookmark** метод определить элементы блока курсора.  
  
 Независимо от того, какой метод использовался для заполнения набора строк и формирования блока курсора [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], этот блок курсора остается активным до выполнения следующего метода извлечения строк применительно к этому набору строк.  
  
## <a name="see-also"></a>См. также  
 [Наборы строк](rowsets.md)  
  
  