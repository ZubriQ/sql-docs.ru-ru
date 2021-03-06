---
title: sys. dm_repl_articles (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_repl_articles_TSQL
- dm_repl_articles
- dm_repl_articles_TSQL
- sys.dm_repl_articles
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_repl_articles dynamic management function
ms.assetid: 794d514e-bacd-432e-a8ec-3a063a97a37b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 07dc611371cbff373fb60036c8c16da6656a8de1
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68088593"
---
# <a name="sysdm_repl_articles-transact-sql"></a>sys.dm_repl_articles (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает информацию об объектах базы данных, опубликованных как статьи в текущей топологии репликации.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**artcache_db_address**|**varbinary(8)**|Адрес кэшируемой структуры базы данных в памяти для базы данных публикации.|  
|**artcache_table_address**|**varbinary(8)**|Адрес кэшируемой структуры таблицы в памяти для статьи публикуемой таблицы.|  
|**artcache_schema_address**|**varbinary(8)**|Адрес кэшируемой структуры схемы статьи в памяти для статьи публикуемой таблицы.|  
|**artcache_article_address**|**varbinary(8)**|Адрес кэшируемой структуры статьи в памяти для статьи публикуемой таблицы.|  
|**artid**|**bigint**|Уникальный идентификатор каждой записи в этой таблице.|  
|**artfilter**|**bigint**|Идентификатор хранимой процедуры, используемой для горизонтального фильтра статьи.|  
|**artobjid**|**bigint**|Идентификатор опубликованного объекта.|  
|**artpubid**|**bigint**|Идентификатор публикации, которой принадлежит статья.|  
|**artstatus**|**tinyint**|Битовая маска параметров и состояния статьи, которая может быть результатом побитовой логической операции ИЛИ над одним или несколькими из этих значений:<br /><br /> **1** = статья активна.<br /><br /> **8** = включить имя столбца в инструкции INSERT.<br /><br /> **16** = использовать параметризованные инструкции.<br /><br /> **24** = оба значения включают имя столбца в инструкции INSERT и используют параметризованные инструкции.<br /><br /> Например, для активной статьи, в которой используются параметризованные инструкции, значение данного столбца должно быть равно 17. Значение 0 указывает, что статья неактивна и никакие дополнительные свойства не определены.|  
|**arttype**|**tinyint**|Тип статьи:<br /><br /> **1** = статья на основе журнала.<br /><br /> **3** = статья на основе журнала с ручным фильтром.<br /><br /> **5** = статья на основе журнала с ручным просмотром.<br /><br /> **7** = статья на основе журнала с ручным фильтром и ручным просмотром.<br /><br /> **8** = выполнение хранимой процедуры.<br /><br /> **24** = выполнение сериализуемых хранимых процедур.<br /><br /> **32** = хранимая процедура (только схема).<br /><br /> **64** = представление (только схема).<br /><br /> **128** = функция (только схема).|  
|**wszArtdesttable**|**nvarchar (514)**|Имя публикуемого объекта на целевом сервере.|  
|**wszArtdesttableowner**|**nvarchar (514)**|Владелец публикуемого объекта на целевом сервере.|  
|**wszArtinscmd**|**nvarchar (510)**|Команда или хранимая процедура, используемая для вставок.|  
|**cmdTypeIns**|**int**|Синтаксис вызова хранимой процедуры вставки. Может принимать следующие значения:<br /><br /> **1** = вызов<br /><br /> **2** = SQL<br /><br /> **3** = нет<br /><br /> **7** = неизвестно|  
|**wszArtdelcmd**|**nvarchar (510)**|Команда или хранимая процедура, используемая для удалений.|  
|**cmdTypeDel**|**int**|Синтаксис вызова хранимой процедуры удаления. Может принимать следующие значения:<br /><br /> **0** = XCALL<br /><br /> **1** = вызов<br /><br /> **2** = SQL<br /><br /> **3** = нет<br /><br /> **7** = неизвестно|  
|**wszArtupdcmd**|**nvarchar (510)**|Команда или хранимая процедура, используемая для обновлений.|  
|**cmdTypeUpd**|**int**|Синтаксис вызова хранимой процедуры обновления. Может принимать следующие значения:<br /><br /> **0** = XCALL<br /><br /> **1** = вызов<br /><br /> **2** = SQL<br /><br /> **3** = нет<br /><br /> **4** = MCALL<br /><br /> **5** = VCALL<br /><br /> **6** = масштабируемый<br /><br /> **7** = неизвестно|  
|**wszArtpartialupdcmd**|**nvarchar (510)**|Команда или хранимая процедура, используемая для частичных обновлений.|  
|**cmdTypePartialUpd**|**int**|Синтаксис вызова хранимой процедуры частичного обновления. Может принимать следующие значения:<br /><br /> **2** = SQL|  
|**numcol**|**int**|Количество столбцов в секции для статьи с вертикальным фильтром.|  
|**artcmdtype**|**tinyint**|Тип реплицируемой в данный момент команды. Может принимать одно из следующих значений:<br /><br /> **1** = вставить<br /><br /> **2** = удалить<br /><br /> **3** = обновление<br /><br /> **4** = UPDATETEXT<br /><br /> **5** = нет<br /><br /> **6** = только для внутреннего использования<br /><br /> **7** = только для внутреннего использования<br /><br /> **8** = ЧАСТИЧНОе обновление|  
|**artgeninscmd**|**nvarchar (510)**|Шаблон команды INSERT, основанный на столбцах, включенных в статью.|  
|**artgendelcmd**|**nvarchar (510)**|Шаблон команды DELETE, который может включать первичный ключ или столбцы, включенные в статью, в зависимости от используемого синтаксиса вызова.|  
|**artgenupdcmd**|**nvarchar (510)**|Шаблон команды UPDATE, который может включать первичный ключ, обновляемые столбцы или полный список столбцов, в зависимости от используемого синтаксиса вызова.|  
|**artpartialupdcmd**|**nvarchar (510)**|Шаблон команды частичного UPDATE, который включает первичный ключ и обновляемые столбцы.|  
|**artupdtxtcmd**|**nvarchar (510)**|Шаблон команды UPDATETEXT, который включает первичный ключ и обновляемые столбцы.|  
|**artgenins2cmd**|**nvarchar (510)**|Шаблон команды INSERT, используемый при согласовании статьи во время параллельной обработки моментальных снимков.|  
|**artgendel2cmd**|**nvarchar (510)**|Шаблон команды DELETE, используемый при согласовании статьи во время параллельной обработки моментальных снимков.|  
|**fInReconcile**|**tinyint**|Определяет, будет ли выполняться согласование статьи во время параллельной обработки моментальных снимков.|  
|**fPubAllowUpdate**|**tinyint**|Определяет, позволяет ли публикация обновляемые подписки.|  
|**intPublicationOptions**|**bigint**|Битовая карта, указывающая дополнительные параметры публикации, со следующими необязательными значениями битов:<br /><br /> **0x1** — включается для одноранговой репликации.<br /><br /> **0x2** — публиковать только локальные изменения.<br /><br /> **0x4** — включено для подписчиков, отличных от SQL Server.|  
  
## <a name="permissions"></a>Разрешения  
 Для вызова **dm_repl_articles**требуется разрешение на просмотр состояния базы данных публикации.  
  
## <a name="remarks"></a>Remarks  
 Возвращаются сведения только по реплицируемым объектам базы данных, которые загружены в кэш статей репликации.  
  
## <a name="see-also"></a>См. также:  
 [Динамические административные представления и функции &#40;&#41;Transact-SQL](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Динамические административные представления, связанные с репликацией &#40;&#41;Transact-SQL](../../relational-databases/system-dynamic-management-views/replication-related-dynamic-management-views-transact-sql.md)  
  
  

