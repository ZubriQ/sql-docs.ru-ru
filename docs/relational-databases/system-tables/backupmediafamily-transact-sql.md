---
title: backupmediafamily (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- backupmediafamily
- backupmediafamily_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- backupmediafamily system table
- backup media [SQL Server], backupmediafamily system table
ms.assetid: ee16de24-3d95-4b2e-a094-78df2514d18a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6ea3fd7937447ba3ed0f3ad89965301dead772cf
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68122881"
---
# <a name="backupmediafamily-transact-sql"></a>backupmediafamily (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит по одной строке для каждого семейства носителей. Если семейство носителей хранится на зеркальном наборе носителей, семейство имеет отдельную строку для каждого зеркала в наборе носителей. Эта таблица хранится в базе данных **msdb** .  
    
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**media_set_id**|**int**|Уникальный идентификатор набора носителей, элементом которого является данное семейство. Ссылается на **backupmediaset (media_set_id)**|  
|**family_sequence_number**|**tinyint**|Позиция семейства носителей в наборе носителей.|  
|**media_family_id**|**uniqueidentifier**|Уникальный идентификатор семейства носителей. Может иметь значение NULL.|  
|**media_count**|**int**|Количество носителей в семействе носителей. Может иметь значение NULL.|  
|**logical_device_name**|**nvarchar(128)**|Имя этого устройства резервного копирования в **sys. backup_devices. Name**. Если это временное устройство резервного копирования (в отличие от постоянного устройства резервного копирования, которое существует в **sys. backup_devices**), значение **logical_device_name** равно null.|  
|**physical_device_name**|**nvarchar(260)**|Физическое имя устройства резервного копирования. Может иметь значение NULL. Это поле совместно используется процессом резервного копирования и восстановления. Он может содержать исходный путь назначения резервной копии или исходный путь восстановления источника. В зависимости от того, выполнялась ли резервное копирование или восстановление на сервере для базы данных. Обратите внимание, что последовательные операции восстановления из одного и того же файла резервной копии не будут обновлять путь независимо от их расположения во время восстановления. Поэтому **physical_device_name** поле нельзя использовать для просмотра используемого пути восстановления.|  
|**device_type**|**tinyint**|Тип устройства резервного копирования:<br /><br /> 2 = диск;<br /><br /> 5 = лента;<br /><br /> 7 = виртуальное устройство<br /><br /> 9 = служба хранилища Azure<br /><br /> 105 = постоянное устройство резервного копирования.<br /><br /> Может иметь значение NULL.<br /><br /> Все постоянные имена устройств и номера устройств можно найти в **sys. backup_devices**.|  
|**physical_block_size**|**int**|Физический размер блока, используемого для записи семейства носителей. Может иметь значение NULL.|  
|**Отображение**|**tinyint**|Номер зеркала (0-3).|  
  
## <a name="remarks"></a>Remarks  
 Инструкция RESTORE VERIFYONLY из *backup_device* with LOADHISTORY заполняет столбцы таблицы **backupmediaset** соответствующими значениями из заголовка набора носителей.  
  
 Чтобы уменьшить количество строк в этой таблице и в других таблицах резервного копирования и журнала, выполните хранимую процедуру [sp_delete_backuphistory](../../relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql.md) .  
  
## <a name="see-also"></a>См. также:  
 [Резервное копирование и восстановление таблиц &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backup-and-restore-tables-transact-sql.md)   
 [backupfile &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupfile-transact-sql.md)   
 [backupfilegroup &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupfilegroup-transact-sql.md)   
 [backupmediaset &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupmediaset-transact-sql.md)   
 [резервный &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupset-transact-sql.md)   
 [Системные таблицы (Transact-SQL)](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
