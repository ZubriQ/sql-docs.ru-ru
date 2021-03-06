---
title: Тестирование взаимодействующих приложений | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC], testing interoperable applications
- testing interoperable applications [ODBC]
ms.assetid: 489083cb-8430-40be-9ef2-d75b9a2eea88
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c1d43c7aad2501591c497475f6c250ac33712aa7
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81307745"
---
# <a name="testing-interoperable-applications"></a>Тестирование приложений с поддержкой взаимодействия
Тестирование взаимодействующих приложений является наилучшим решением, требующим много времени, и наихудшим невозможным, поскольку на рынке постоянно появляются новые драйверы. Тем не менее, возможна разумная степень тестирования. Приложения с ограниченной или низкой совместимостью необходимо тестировать только на тех драйверах, поддержка которых гарантируется. Однако они должны быть полностью протестированы с этими драйверами.  
  
 Приложения с высоким уровнем взаимодействия не могут быть проверены практически на всех драйверах. Наилучшим решением для большинства разработчиков приложений является их полное тестирование с небольшим количеством драйверов и курсорили. Проверенные драйверы должны включать самые популярные драйверы для наиболее популярных СУБД на рынке приложения. Если на рынке все СУБД, необходимо протестировать драйверы для серверных и системных СУБД.  
  
 Одной из проблем при тестировании приложений ODBC является количество задействованных компонентов: само приложение, диспетчер драйверов, драйвер, СУБД и, возможно, сетевое программное обеспечение или шлюзы. Приложения могут упростить отслеживание ошибок, отправляя сообщения об ошибках, возвращаемые функциями ODBC, с помощью **SQLGetDiagField** и **SQLGetDiagRec**. Эти сообщения указывают изготовителя и компонент, в которых возникают ошибки. Дополнительные сведения см. в разделе [Диагностика](../../../odbc/reference/develop-app/diagnostics.md).
