---
title: backupmediaset (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- backupmediaset
- backupmediaset_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- backup media [SQL Server], backupmediaset system table
- backupmediaset system table
ms.assetid: d9c18a93-cab9-4db8-ae09-c6bd8145ab8f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1dbaf429acb94334540f0e147eae2808e1655309
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68119347"
---
# <a name="backupmediaset-transact-sql"></a>backupmediaset (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит по одной строке для каждого резервного набора носителей. Эта таблица хранится в базе данных **msdb** .  
 
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**media_set_id**|**int**|Уникальный идентификационный номер набора носителей. Удостоверение, первичный ключ.|  
|**media_uuid**|**uniqueidentifier**|UUID набора носителей. Все [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] наборы носителей имеют UUID.<br /><br /> Однако в более ранних версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], если набор носителей содержит только одно семейство носителей, столбец **media_uuid** может иметь значение null (**media_family_count** равен 1).|  
|**media_family_count**|**tinyint**|Число семейств носителей в наборе носителей. Может иметь значение NULL.|  
|**name**|**nvarchar(128)**|Имя набора носителей. Может иметь значение NULL.<br /><br /> Дополнительные сведения см. в разделе MEDIANAME и MEDIADESCRIPTION в [BACKUP &#40;Transact-SQL&#41;](../../t-sql/statements/backup-transact-sql.md).|  
|**nописание**|**nvarchar(255)**|Текстовое описание набора носителей. Может иметь значение NULL.<br /><br /> Дополнительные сведения см. в разделе MEDIANAME и MEDIADESCRIPTION в [BACKUP &#40;Transact-SQL&#41;](../../t-sql/statements/backup-transact-sql.md).|  
|**software_name**|**nvarchar(128)**|Имя программного обеспечения резервного копирования, которое записало метку носителя. Может иметь значение NULL.|  
|**software_vendor_id**|**int**|Идентификационный номер поставщика программного обеспечения, которое записало метку носителя резервной копии. Может иметь значение NULL.<br /><br /> Значение для [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] параметра является шестнадцатеричным 0x1200.|  
|**MTF_major_version**|**tinyint**|Главный номер версии формата ленты [!INCLUDE[msCoName](../../includes/msconame-md.md)], используемого для формирования этого набора носителей. Может иметь значение NULL.|  
|**mirror_count**|**tinyint**|Число зеркальных отображений в наборе носителей.|  
|**is_password_protected**|**bit**|Защищен ли набор носителей паролем.<br /><br /> 0 = не защищен<br /><br /> 1 = защищен|  
|**is_compressed**|**bit**|Указывает, является ли резервная копия сжатой:<br /><br /> 0 = не сжатая<br /><br /> 1 = сжатая<br /><br /> При обновлении базы данных **msdb** этому параметру присваивается значение null. Это означает резервное копирование без сжатия.|  
|**is_encrypted**|**Версий**|Указывает, шифруется ли резервная копия.<br /><br /> 0 = не зашифрована<br /><br /> 1 = зашифрована|  
  
## <a name="remarks"></a>Remarks  
 Инструкция RESTORE VERIFYONLY из *backup_device* with LOADHISTORY заполняет столбцы таблицы **backupmediaset** соответствующими значениями из заголовка набора носителей.  
  
 Чтобы уменьшить количество строк в этой таблице и в других таблицах резервного копирования и журнала, выполните хранимую процедуру [sp_delete_backuphistory](../../relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql.md) .  
  
## <a name="see-also"></a>См. также:  
 [Резервное копирование и восстановление таблиц &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backup-and-restore-tables-transact-sql.md)   
 [backupfile &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupfile-transact-sql.md)   
 [backupfilegroup &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupfilegroup-transact-sql.md)   
 [backupmediafamily &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupmediafamily-transact-sql.md)   
 [резервный &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupset-transact-sql.md)   
 [Системные таблицы (Transact-SQL)](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
