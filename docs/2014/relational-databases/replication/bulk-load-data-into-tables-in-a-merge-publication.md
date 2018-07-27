---
title: Массовая загрузка данных в таблицы в публикации слиянием (Программирование репликации Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- bulk load [SQL Server replication]
- merge replication bulk loading [SQL Server replication]
- sp_addtabletocontents
ms.assetid: 16e6498a-b449-4051-aec4-ea814a2ad993
caps.latest.revision: 32
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 5fe31b5f7720896c149af4463de3ef9a72cae23b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37166975"
---
# <a name="bulk-load-data-into-tables-in-a-merge-publication-replication-transact-sql-programming"></a>выполнить массовую загрузку данных в таблицы при публикации слиянием (программирование репликации на языке Transact-SQL)
  При загрузке данных в таблицы с использованием методов, описанных в разделе [bcp Utility](../../tools/bcp-utility.md) , или инструкцией [BULK INSERT](/sql/t-sql/statements/bulk-insert-transact-sql) триггеры репликации слиянием, которые обеспечивают отслеживание данных в системной таблице [MSmerge_contents](/sql/relational-databases/system-tables/msmerge-contents-transact-sql) , выполняться не будут. В этом случае можно либо принудительно выполнять в процессе загрузки данных триггеры репликации слиянием, либо с помощью хранимых процедур репликации программным путем вставить созданные метаданные репликации после завершения массового копирования.  
  
### <a name="to-bulk-load-data-into-tables-published-by-merge-replication-using-the-bcp-utility"></a>Массовая загрузка данных в таблицы, публикуемые в репликации слиянием с помощью программы bcp  
  
1.  На издателе или на подписчике запустите программу [bcp Utility](../../tools/bcp-utility.md) или выполните инструкцию [BULK INSERT](/sql/t-sql/statements/bulk-insert-transact-sql) , чтобы вставить данные в таблицу, публикуемую в репликации слиянием.  
  
2.  Одним из следующих методов сформируйте для вставленных данных метаданные репликации.  
  
    -   Выполните операцию массового копирования с параметром FIRE_TRIGGERS.  
  
    -   В базе данных, в которую вставлены данные, выполните процедуру [sp_addtabletocontents (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addtabletocontents-transact-sql). Укажите в параметре **@table_name**.  
  
  