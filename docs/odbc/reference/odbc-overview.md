---
title: Обзор ODBC | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC [ODBC]
- ODBC [ODBC], about ODBC
ms.assetid: 233315bd-2b7f-4b20-9978-e920e1ea9a07
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0a0515a882cd7d1c97a60e9262942bd7c397b0b2
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81298294"
---
# <a name="odbc-overview"></a>Общие сведения об ODBC
ODBC — это широко принятый интерфейс прикладного программирования (API) для доступа к базе данных. Он основан на спецификациях интерфейса уровня вызовов (CLI) из Open Group и ISO/IEC для API-интерфейсов баз данных и использует язык SQL (SQL) в качестве языка доступа к базе данных.  
  
 ODBC предназначен для обеспечения максимальной *совместимости* , то есть возможности одного приложения обращаться к разным системам управления базами данных (СУБД) с помощью одного и того же исходного кода. Приложения базы данных вызывают функции в интерфейсе ODBC, которые реализуются в модулях, связанных с базами данных, которые называются *драйверами*. Использование драйверов изолирует приложения от вызовов, зависящих от базы данных, так же, как драйверы принтера изолируют программы обработки текста от команд, относящихся к принтеру. Поскольку драйверы загружаются во время выполнения, пользователю нужно только добавить новый драйвер для доступа к новой СУБД. перекомпиляция или повторная привязка приложения не требуется.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Зачем создали ODBC?](../../odbc/reference/why-was-odbc-created.md)  
  
-   [Что такое ODBC?](../../odbc/reference/what-is-odbc.md)  
  
-   [ODBC и стандартная инфраструктура CLI](../../odbc/reference/odbc-and-the-standard-cli.md)
