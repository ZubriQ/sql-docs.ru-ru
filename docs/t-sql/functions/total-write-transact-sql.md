---
title: '@@TOTAL_WRITE (Transact-SQL) | Документы Майкрософт'
ms.custom: ''
ms.date: 09/18/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- '@@TOTAL_WRITE'
- '@@TOTAL_WRITE_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- write activity since last started [SQL Server]
- number of disk writes
- '@@TOTAL_WRITE function'
- disks [SQL Server], number of disk writes
- total write [SQL Server]
ms.assetid: cd528126-51ee-4aa4-a21f-f32ce5c80fac
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 295dbd375b099227fb29333a3af925649b1fb88e
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "68098922"
---
# <a name="x40x40total_write-transact-sql"></a>&#x40;&#x40;TOTAL_WRITE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает число операций записи на диск, выполненных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с момента последнего запуска [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
@@TOTAL_WRITE  
```  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 **integer**  
  
## <a name="remarks"></a>Remarks  
 Для отображения отчета, содержащего несколько статистик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], в том числе действий чтения и записи, выполните процедуру **sp_monitor**.  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращается общее количество операций чтения и записи на диске до текущей даты и времени.  
  
```  
SELECT @@TOTAL_READ AS 'Reads', @@TOTAL_WRITE AS 'Writes', GETDATE() AS 'As of'  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Reads       Writes      As of                   
----------- ----------- ----------------------  
7760        97263       12/5/2006 10:23:00 PM   
```  
  
## <a name="see-also"></a>См. также:  
 [sp_monitor (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-monitor-transact-sql.md)   
 [Системные статистические функции (Transact-SQL)](../../t-sql/functions/system-statistical-functions-transact-sql.md)   
 [@@TOTAL_READ &#40;Transact-SQL&#41;](../../t-sql/functions/total-read-transact-sql.md)  
  
  
