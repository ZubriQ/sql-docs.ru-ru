---
title: Синтаксис команд | Документация Майкрософт
description: Синтаксис команд и хранимые процедуры.
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, commands
- commands [OLE DB]
- OLE DB Driver for SQL Server, stored procedures
- stored procedures [OLE DB], command syntax
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 15d6d221c9e3435a3ba4c3f58c7d6b6e55314f29
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "68016118"
---
# <a name="command-syntax"></a>Синтаксис команды
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  OLE DB Driver for SQL Server распознает синтаксис команд, определенный макросом DBGUID_SQL. Описатель сообщает OLE DB Driver for SQL Server, что сочетание ODBC SQL, ISO и [!INCLUDE[tsql](../../../includes/tsql-md.md)] является допустимым синтаксисом. Например, следующая инструкция SQL использует escape-последовательность ODBC SQL, чтобы указать строковую функцию LCASE.  
  
```  
SELECT customerid={fn LCASE(CustomerID)} FROM Customers  
```  
  
 Функция LCASE возвращает строковое выражение, в котором все символы приведены к нижнему регистру. Строковая функция LOWER стандарта ISO выполняет ту же операцию, поэтому следующая инструкция SQL является эквивалентом ISO для представленной выше инструкции ODBC.  
  
```  
SELECT customerid=LOWER(CustomerID) FROM Customers  
```  
  
 Драйвер OLE DB для SQL Server успешно обрабатывает любую форму инструкции при указании в виде текста для команды.  
  
## <a name="stored-procedures"></a>Хранимые процедуры  
 При выполнении хранимой процедуры [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с помощью команды драйвера OLE DB для SQL Server используйте escape-последовательность ODBC CALL в тексте команды. В этом случае драйвер OLE DB для SQL Server использует механизм удаленного вызова процедуры [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], чтобы оптимизировать обработку команды. Например, следующая инструкция ODBC SQL является более предпочтительным текстом команды, нежели форма [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
-   ODBC SQL  
  
    ```  
    {call SalesByCategory('Produce', '1995')}  
    ```  
  
-   Transact-SQL  
  
    ```  
    EXECUTE SalesByCategory 'Produce', '1995'  
    ```  
  
## <a name="see-also"></a>См. также:  
 [Команды](../../oledb/ole-db-commands/commands.md)  
  
  
