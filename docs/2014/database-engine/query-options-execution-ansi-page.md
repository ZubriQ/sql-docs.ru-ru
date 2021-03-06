---
title: Выполнение параметров запроса (страница ANSI) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.swb.query.ansi.f1
ms.assetid: c90d7cdf-3309-46f4-b900-220521bb9552
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: d9a8b5dea5ab90137c95c9ddaf609c63532dd5b1
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66089082"
---
# <a name="query-options-execution-ansi-page"></a>Выполнение параметров запроса (страница ANSI)
  Используйте эту страницу, чтобы указать [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , что будет выполнять запросы, используя все параметры или часть параметров, указанных в стандарте ISO (ANSI).  
  
## <a name="uielement-list"></a>Список элементов пользовательского интерфейса  
 **SET ANSI_DEFAULTS**  
 Выбор всех параметров ISO по умолчанию. Этот флажок по умолчанию недоступен, так как настроены только некоторые параметры ISO.  
  
 **SET QUOTED_IDENTIFIER**  
 Заключение идентификаторов объектов в кавычки. Этот параметр установлен по умолчанию.  
  
 **SET ANSI_NULL_DFLT_ON**  
 Разрешение значений NULL для всех пользовательских типов данных или столбцов, которые не определены явно как NOTNULL в инструкции CREATE TABLE или ALTER TABLE (состояние по умолчанию). Этот параметр установлен по умолчанию.  
  
 **SET IMPLICIT_TRANSACTIONS**  
 Этот параметр выключен по умолчанию.  
  
 **SET CURSOR_CLOSE_ON_COMMIT**  
 Автоматическое закрытие всех открытых курсоров (в соответствии с ISO) после фиксации транзакции. Сброшенные (переведенные в состояние OFF) курсоры остаются открытыми между транзакциями и закрываются, только когда закрывается соединение или при явном закрытии курсоров. Этот параметр выключен по умолчанию.  
  
 **SET ANSI_PADDING**  
 Управляет тем, как столбец хранит значения короче, чем определенный размер столбца, а также способ хранения в нем значений с конечными пробелами в данных **типа char**, **varchar**, **binary**и **varbinary** . Этот параметр влияет только на определение новых столбцов. После создания столбца [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] сохраняет значения, исходя из значения параметра на время создания столбца. Более поздние изменения этого параметра не влияют на существующие столбцы. Этот флажок выбран по умолчанию.  
  
 **SET ANSI_WARNINGS**  
 Задает поведение в соответствии со стандартом ISO для некоторых условий ошибок:  
  
-   При установке флажка, если в агрегатных функциях (SUM, AVG, MAX, MIN, STDEV, STDEVP, VAR, VARP или COUNT) встречаются значения NULL, создается предупреждение. Если задано **Off**, предупреждение не выдается.  
  
-   Если флажок снят, ошибки деления на ноль и переполнения при выполнении арифметических операций приводят к откату инструкции и выдаче сообщения об ошибке. Если выбрано значение OFF, при возникновении ошибок деления на ноль и переполнения при выполнении арифметических операций возвращается значение NULL. Поведение, при котором в случае ошибки деления на ноль или переполнения при выполнении арифметических операций возвращается значение NULL, возникает при попытке выполнения операции INSERT или UPDATE с символьным, двоичным столбцом или столбцом в Юникоде, если длина нового значения превышает максимальный размер столбца. Если **параметр SET ANSI_WARNINGS имеет значение** on, операция вставки или обновления отменяется, как указано стандартом ISO. Завершающие пробелы игнорируются для символьных столбцов, а завершающие значения NULL игнорируются для двоичных столбцов. Если указано значение OFF, то данные усекаются до размера столбца, и инструкция успешно завершается.  
  
 Этот параметр установлен по умолчанию.  
  
 **SET ANSI_NULLS**  
 Позволяет задать совместимое со стандартом ISO поведение операторов сравнения «Равно» (`=`) и «Не равно» (`<>`) при использовании со значениями NULL. Если флажок **SET ANSI_NULLS** установлен, то результатом сравнений любых значений со значением NULL оказывается значение UNKNOWN в соответствии со стандартом ISO. Если параметр **SET ANSI_NULLS** не выбран, то результатом сравнений данных со значением NULL становится значение TRUE, если данные имеют значение NULL. Этот параметр установлен по умолчанию.  
  
 **По умолчанию**  
 Позволяет вернуть исходные значения по умолчанию для всех параметров на данной странице.  
  
  
