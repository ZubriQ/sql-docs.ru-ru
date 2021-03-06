---
title: Монитор активности | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Activity Monitor [SQL Server]
ms.assetid: 1e6c430d-3a2a-468e-a3d5-ef5459c36c15
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: f2420a4df5b971ae2190b2a66f24b226f472fee2
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "63249342"
---
# <a name="activity-monitor"></a>Монитор активности
  Монитор активности отображает сведения о процессах [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и о том, как функционирование этих процессов влияет на текущий экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="benefits-of-activity-monitor"></a>Преимущества монитора активности  
 Монитор активности — это окно документов с вкладками со следующими развертываемыми и свертываемыми панелями: **Общие сведения**, **Активные пользовательские задачи**, **Ожидание ресурсов**, **Ввод-вывод в файл данных**и **Последние ресурсоемкие запросы**. После развертывания любой панели монитор активности выполняет запрос к экземпляру для получения необходимых сведений. При свертывании панели выполнение всех операций запроса для этой панели приостанавливается. Также можно одновременно развернуть одну или более панелей для просмотра различных типов активности в экземпляре.  
  
 Для столбцов на панели **Активные пользовательские задачи**, **Ожидание ресурсов**, **Ввод-вывод в файл данных**и **Последние ресурсоемкие запросы** можно настроить отображение следующим образом.  
  
1.  Чтобы изменить порядок столбцов, щелкните заголовок столбца и перетащите его в другое место ленты заголовков.  
  
2.  Чтобы отсортировать столбец, щелкните имя столбца.  
  
3.  Чтобы выполнить фильтрацию по одному или нескольким столбцам, щелкните стрелку раскрывающегося списка в заголовке столбца и выберите значение.  
  
## <a name="related-tasks"></a>Связанные задачи  
 Используйте следующие задачи, чтобы начать работу с монитором активности:  
  
|||  
|-|-|  
|**Описание**|**Раздел**|  
|Содержит сведения о том, как открыть монитор активности и настроить интервал обновления монитора активности.|[Открытие монитора активности (среда SQL Server Management Studio)](../performance-monitor/open-activity-monitor-sql-server-management-studio.md)|  
|Ссылки на разделы с описанием производительности сервера и отслеживания действий.|[Мониторинг производительности и действий сервера](../performance/server-performance-and-activity-monitoring.md)|  
  
  
