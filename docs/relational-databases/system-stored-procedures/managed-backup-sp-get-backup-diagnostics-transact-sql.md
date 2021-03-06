---
title: managed_backup. sp_get_backup_diagnostics (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_get_backup_diagnostics_TSQL
- sp_get_backup_diagnostics
- smart_admin.sp_get_backup_diagnostics_TSQL
- smart_admin.sp_get_backup_diagnostics
dev_langs:
- TSQL
helpviewer_keywords:
- sp_get_backup_diagnostics
- smart_admin.sp_get_backup_diagnostics
ms.assetid: 2266a233-6354-464b-91ec-824ca4eb9ceb
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5e967ae5b46ec703da4e8b1fff64f298fdf8a081
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67942048"
---
# <a name="managed_backupsp_get_backup_diagnostics-transact-sql"></a>managed_backup. sp_get_backup_diagnostics (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Возвращает расширенные события, записанные в журнал объектом Smart Admin.  
  
 Используйте эту хранимую процедуру для мониторинга расширенных событий, регистрируемых интеллектуальным администратором. [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] события регистрируются в этой системе и могут быть просмотрены и отслеживаться с помощью этой хранимой процедуры.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
managed_backup.sp_get_backup_diagnostics [@xevent_channel = ] 'event type' [, [@begin_time = ] 'time1' ] [, [@end_time = ] 'time2'VARCHAR(255) = 'Xevent',@begin_time DATETIME = NULL,@end_time DATETIME = NULL  
```  
  
##  <a name="arguments"></a><a name="Arguments"></a>Даваемых  
 @xevent_channel  
 Тип расширенного события. Значение по умолчанию предполагает возврат всех событий, занесенных в журнал за предшествующие 30 минут. Занесенные в журнал события зависят от типа включенных расширенных событий. Этот параметр можно использовать для фильтрации хранимой процедуры, чтобы показывать только события определенного типа. Можно либо указать полное имя события, либо указать подстроку, такую как: **"admin** **", "Analytics"**, "Operation **"** и **"Debug"**. @event_channel Имеет тип **varchar (255)**.  
  
 Чтобы получить список типов событий, включенных в данный момент, используйте функцию **managed_backup. fn_get_current_xevent_settings** .  
  
 [@begin_time  
 Начало периода времени, события из которого должны отображаться. @begin_time Параметр имеет тип DateTime и значение по умолчанию NULL. Если не задан, отображаются события за последние 30 минут.  
  
 @end_time  
 Конец периода времени, события из которого должны отображаться. @end_time Параметр имеет значение Time со значением по умолчанию NULL.  Если не задан, отображаются события по текущий момент.  
  
## <a name="table-returned"></a>Возвращаемая таблица  
 Эта хранимая процедура возвращает таблицу со следующей информацией:  
  
||||  
|-|-|-|  
|Имя столбца|Тип данных|Описание|  
|event_type|NVARCHAR (512)|Тип расширенного события.|  
|событие|NVARCHAR (512)|Сводка журналов событий.|  
|Отметка времени|timestamp|Отметка времени события, показывающая, когда оно возникло.|  
  
## <a name="security"></a>Безопасность  
  
### <a name="permissions"></a>Разрешения  
 Требуются разрешения **EXECUTE** на хранимую процедуру. Также требуется разрешение **View Server State** , так как оно внутренне вызывает другие системные объекты, требующие этого разрешения.  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращаются все события, записанные за последние 30 минут  
  
```  
Use msdb  
Go  
EXEC managed_backup.sp_get_backup_diagnostics  
  
```  
  
 В следующем примере возвращаются все события, записанные за указанный отрезок времени.  
  
```  
Use msdb  
Go  
EXEC managed_backup.sp_get_backup_diagnostics @xevent_channel = 'Admin',  
  @begin_time = '2013-06-01', @end_time = '2013-06-10'  
  
```  
  
 В следующем примере возвращаются все аналитические события, записанные за последние 30 минут  
  
```  
Use msdb  
Go  
EXEC managed_backup.sp_get_backup_diagnostics @xevent_channel = 'Analytic'  
  
```  
  
  
