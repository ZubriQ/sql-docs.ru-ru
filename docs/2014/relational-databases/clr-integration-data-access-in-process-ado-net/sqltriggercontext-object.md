---
title: Объект SqlTriggerContext | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- SqlTriggerContext object
- triggers [CLR integration]
- context [CLR integration]
ms.assetid: 472a2d0b-64ae-4877-8f11-a5620aa698b7
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: df384324ba16aac03a4c889cf4f3959c23374510
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "62874689"
---
# <a name="sqltriggercontext-object"></a>SqlTriggerContext, объект
  Класс `SqlTriggerContext` предоставляет сведения контекста о триггере. В сведения о контексте включают тип действия, вызвавшего срабатывание триггера, столбцы, измененные в рамках операции UPDATE, а в случае триггера DDL — структуру XML `EventData`, которая описывает операцию триггера. Дополнительные сведения и примеры использования `SqlTriggerContext` класса см. в разделе [триггеры CLR](../../database-engine/dev-guide/clr-triggers.md).  
  
 Дополнительные сведения см. в справочной документации по классу `Microsoft.SqlServer.Server.SqlTriggerContext` в документации по пакету .NET Framework SDK.  
  
## <a name="see-also"></a>См. также  
 [Триггеры CLR](../../database-engine/dev-guide/clr-triggers.md)   
 [EVENTDATA (Transact-SQL)](/sql/t-sql/functions/eventdata-transact-sql)  
  
  
