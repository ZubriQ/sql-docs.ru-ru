---
title: Процедуры | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- stored procedures [ODBC]
- stored procedures [ODBC], about ODBC stored procedures
- ODBC applications, statements
- statements [ODBC], stored procedures
- ODBC applications, stored procedures
ms.assetid: c64d5f3a-376b-48ef-84f3-b6148ac8600a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d030d4fb12ce9217bbdb88f501a0b0674c5a5828
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "68206748"
---
# <a name="procedures"></a>Процедуры
  Хранимая процедура представляет собой заранее скомпилированный исполняемый объект, содержащий одну или несколько инструкций [!INCLUDE[tsql](../../../includes/tsql-md.md)]. Хранимые процедуры могут иметь входные и выходные параметры, а также возвращать целочисленный код возврата. Приложение может перечислять существующие хранимые процедуры с помощью функций для работы с каталогами.  
  
 Приложения ODBC для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] должны вызывать хранимые процедуры только методом прямого выполнения. При подключении к более ранним [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]версиям [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] драйвер ODBC для собственного клиента реализует [функцию SQLPrepare](https://go.microsoft.com/fwlink/?LinkId=59360) , создавая временную хранимую процедуру, которая затем вызывается в **SQLExecute**. Он добавляет дополнительные издержки, чтобы **SQLPrepare** создать временную хранимую процедуру, которая вызывает только целевую хранимую процедуру и не выполняет непосредственное выполнение целевой хранимой процедуры. Даже если соединение с базой данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] уже существует, подготовка вызова требует лишнего цикла приема-передачи данных по сети и построения плана выполнения, который только вызывает план выполнения хранимой процедуры.  
  
 При выполнении хранимой процедуры приложения ODBC должны использовать конструкцию ODBC CALL. Драйвер оптимизирован так, что при обработке конструкции ODBC CALL использует механизм удаленного вызова процедур (RPC). Это эффективнее, чем механизм, используемый для посылки инструкции [!INCLUDE[tsql](../../../includes/tsql-md.md)] EXECUTE на сервер.  
  
 Дополнительные сведения см. в разделе [выполнение хранимых процедур](../../native-client-odbc-stored-procedures/running-stored-procedures.md).  
  
## <a name="see-also"></a>См. также  
 [Исполнение инструкций &#40;ODBC&#41;](executing-statements-odbc.md)  
  
  
