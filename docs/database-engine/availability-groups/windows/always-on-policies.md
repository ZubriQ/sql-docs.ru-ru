---
title: Использование политик групп для определения работоспособности группы доступности
description: Сведения о просмотре системных политик групп, используемых панелью мониторинга Always On для предоставления сведений о работоспособности групп доступности.
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
ms.assetid: 26bf8f71-c2b8-45ef-b3a3-372b96c9e6e3
author: rothja
ms.author: jroth
ms.openlocfilehash: 6a48450322a8552720a119ea325ed720669fe5a8
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "75245652"
---
# <a name="evaluate-health-of-the-always-on-availability-group-using-group-policies"></a>Определение работоспособности группы доступности Always On с помощью групповых политик
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Системные политики для групп доступности Always On используются на панели мониторинга Always On для предоставления пользователю информации о работоспособности групп доступности. Они очень удобны для первоначального устранения неполадок в работе групп доступности. Эти политики можно расширять и использовать для настройки панели мониторинга AlwaysOn, а также оперативно выполнять для получения нужных сведений о работоспособности.  
  
 Существует 14 системных политик для групп доступности. Подробные сведения о каждой политике см. в разделе [Политики AlwaysOn на случай проблем в работе с группами доступности AlwaysOn (SQL Server)](always-on-policies-for-operational-issues-always-on-availability.md).  
  
## <a name="view-or-evaluate-availability-groups-system-policies"></a>Просмотр и оценка системных политик для групп доступности  
 Для просмотра или выполнения системных политик групп доступности в SQL Server Management Studio (SSMS) сделайте следующее:  
  
1.  В **обозревателе объектов** последовательно разверните узлы **Управление**, **Управление политиками**, **Политики** и **Системные политики**.  
  
2.  Щелкните правой кнопкой мыши одну из политик и выберите **Вычислить**. Если вы хотите оценить выбранную политику, больше ничего не требуется. Можно щелкнуть элемент **Просмотреть** в области **Данные целевого объекта**, чтобы просмотреть сведения о результатах оценки.  
  
3.  Чтобы просмотреть все системные политики групп доступности, в области **Выбор страницы** щелкните элемент **Выбор политики**.  
  
## <a name="next-steps"></a>Дальнейшие действия  
 [Модель работоспособности AlwaysOn, часть 2. Расширение модели работоспособности](https://blogs.msdn.com/b/sqlalwayson/archive/2012/02/13/extending-the-alwayson-health-model.aspx)   
  
  
