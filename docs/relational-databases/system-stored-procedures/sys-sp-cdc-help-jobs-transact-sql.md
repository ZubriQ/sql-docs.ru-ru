---
title: sys. sp_cdc_help_jobs (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_cdc_help_jobs
- sys.sp_cdc_help_jobs_TSQL
- sp_cdc_help_jobs_TSQL
- sys.sp_cdc_help_jobs
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cdc_help_jobs
ms.assetid: 9399b4bc-8293-408f-b3cb-f904e0657fb5
author: rothja
ms.author: jroth
ms.openlocfilehash: 9820476ecdee25551d09c8206595b637421b9efd
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68083725"
---
# <a name="syssp_cdc_help_jobs-transact-sql"></a>sys.sp_cdc_help_jobs (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Выдает сведения о всех заданиях очистки системы отслеживания измененных данных и заданиях записи в текущей базе данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sys.sp_cdc_help_jobs  
```  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**job_id**|**uniqueidentifier**|Идентификатор задания.|  
|**job_type**|**nvarchar (20)**|Тип задания.|  
|**maxtrans**|**int**|Максимальное количество транзакций, обрабатываемое в каждом цикле просмотра.<br /><br /> **maxtrans** является допустимым только для заданий отслеживания.|  
|**maxscans**|**int**|Максимальное количество циклов просмотра, выполняемых для извлечения всех строк из журнала.<br /><br /> **maxscans** является допустимым только для заданий отслеживания.|  
|**обеспечения**|**bit**|Флаг, указывающий, следует ли выполнять задание записи непрерывно (1) или запускать однократно (0). Дополнительные сведения см. в разделе [sys. sp_cdc_add_job &#40;&#41;Transact-SQL ](../../relational-databases/system-stored-procedures/sys-sp-cdc-add-job-transact-sql.md).<br /><br /> **Непрерывная** допустима только для заданий отслеживания.|  
|**PollingInterval**|**bigint**|Число секунд между циклами просмотра журнала.<br /><br /> **PollingInterval** является допустимым только для заданий отслеживания.|  
|**хранения**|**bigint**|Число минут, в течение которого строки изменений нужно хранить в таблицах изменений.<br /><br /> **Хранение** допустимо только для заданий очистки.|  
|**значениями**|**bigint**|Максимальное число записей, подлежащих удалению, которые могут быть удалены с помощью одной инструкции при очистке.|  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в предопределенной роли базы данных **db_owner** .  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращаются данные об определенных заданиях отслеживания и очистки для базы данных `AdventureWorks2012`.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sys.sp_cdc_help_jobs;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [dbo. cdc_jobs &#40;Transact-SQL&#41;](../../relational-databases/system-tables/dbo-cdc-jobs-transact-sql.md)   
 [sys.sp_cdc_add_job (Transact-SQL)](../../relational-databases/system-stored-procedures/sys-sp-cdc-add-job-transact-sql.md)  
  
  
