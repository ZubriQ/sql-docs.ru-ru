---
title: IHextendedArticleView (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- IHextendedArticleView_TSQL
- IHextendedArticleView
dev_langs:
- TSQL
helpviewer_keywords:
- IHextendedArticleView view
ms.assetid: 19ef0a12-3214-4bb0-9c25-a665897e65a2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0abca8ca826ec986a9cbf71f4fb577291e095e39
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68029544"
---
# <a name="ihextendedarticleview-transact-sql"></a>IHextendedArticleView (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Представление **IHextendedArticleView** предоставляет сведения о статьях в публикации, отличной от SQL Server. Это представление хранится в базе данных **распространителя** .  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**publisher_id**|**smallint**|Уникальный идентификатор издателя.|  
|**publication_id**|**int**|Уникальный идентификатор публикации.|  
|**рассмотрен**|**sysname**|Имя статьи.|  
|**destination_object**|**sysname**|Имя объекта, опубликованного на стороне подписчика.|  
|**source_owner**|**sysname**|Владелец объекта, опубликованного на стороне издателя.|  
|**source_object**|**sysname**|Имя объекта, опубликованного на стороне издателя.|  
|**nописание**|**nvarchar(255)**|Описание статьи.|  
|**creation_script**|**nvarchar(255)**|Скрипт создания схемы для статьи.|  
|**del_cmd**|**nvarchar(255)**|Команда, выполняемая для инструкции DELETE.|  
|**Фильтрация**|**int**|Идентификатор хранимой процедуры, с помощью которого определяется горизонтальная секция.|  
|**filter_clause**|**ntext**|Предложение WHERE, которое применяется для горизонтальной фильтрации статьи.|  
|**ins_cmd**|**nvarchar(255)**|Команда, выполняемая для инструкции INSERT.|  
|**pre_creation_cmd**|**tinyint**|Команда, выполняемая перед инструкциями DROP TABLE, DELETE TABLE или TRUNCATE:<br /><br /> **0** = нет.<br /><br /> **1** = удалить.<br /><br /> **2** = удалить.<br /><br /> **3** = усечение.|  
|**status**|**tinyint**|Битовая маска параметров и состояния статьи, которая может быть результатом операции побитового логического ИЛИ над одним или несколькими из следующих значений:<br /><br /> **1** = статья активна.<br /><br /> **8** = включить имя столбца в инструкции INSERT.<br /><br /> **16** = использовать параметризованные инструкции.<br /><br /> **24** = оба значения включают имя столбца в инструкции INSERT и используют параметризованные инструкции.<br /><br /> Например, активная статья, использующая параметризованные инструкции, будет иметь значение **17** в этом столбце. Значение **0** означает, что статья неактивна и дополнительные свойства не определены.|  
|**type**|**tinyint**|Тип статьи:<br /><br /> **1** = статья на основе журнала.<br /><br /> **3** = статья на основе журнала с ручным фильтром.<br /><br /> **5** = статья на основе журнала с ручным просмотром.<br /><br /> **7** = статья на основе журнала с ручным фильтром и ручным просмотром.|  
|**upd_cmd**|**nvarchar(255)**|Команда, выполняемая для инструкции UPDATE.|  
|**schema_option**|**binary**|Указывает, что должно быть включено в скрипт. Список поддерживаемых параметров схемы см. в разделе [sp_addarticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md) .|  
|**dest_owner**|**sysname**|Владелец объекта, опубликованного в целевой базе данных.|  
  
## <a name="see-also"></a>См. также:  
 [Разнородная репликация базы данных](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Таблицы репликации &#40;&#41;Transact-SQL](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
