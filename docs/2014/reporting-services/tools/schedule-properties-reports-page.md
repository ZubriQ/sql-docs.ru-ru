---
title: Свойства расписания (страница "Отчеты") | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.scheduleproperties.reports.f1
ms.assetid: 7db728bd-4b08-43ef-a49a-e8dcdd37cf89
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 08fc68575e2515907f31e82cf3609d73da1c95d6
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66099787"
---
# <a name="schedule-properties-reports-page"></a>Свойства расписания (страница отчетов)
  Эта страница используется для просмотра списка всех отчетов, использующих общее расписание. Расписания могут использоваться для обновления моментальных снимков отчетов, формирования журнала отчета, запуска подписки или истечения срока действия кэшированной копии отчета. Сведения об использовании расписания можно найти в свойствах и сведениях о подписке на отчет.  
  
 Несмотря на то, что на данной странице отображаются все отчеты, в которых используется общее расписание, здесь не указывается, сколько раз общее расписание используется в рамках отдельного отчета. Например, предположим, что есть 20 различных подписчиков отчета «Продажи компании» (Company Sales), использующих для запуска обработки подписки одно и то же общее расписание. В этом случае в упомянутом списке отчет «Продажи компании» (Company Sales) будет указан лишь один раз, несмотря на то, что в отчете имеется 20 ссылок на общее расписание.  
  
 Чтобы открыть эту страницу, запустите среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], подключитесь к серверу отчетов, откройте папку **Общие расписания** , щелкните одно из общих расписаний правой кнопкой мыши, выберите пункт **Свойства**, после чего нажмите кнопку **Отчеты**.  
  
> [!NOTE]  
>  Эта функция поддерживается не во всех выпусках [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Список функций [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], поддерживаемых различными выпусками, см. [в разделе функции, поддерживаемые различными выпусками SQL Server 2012](https://go.microsoft.com/fwlink/?linkid=232473) (https://go.microsoft.com/fwlink/?linkid=232473).  
  
## <a name="options"></a>Параметры  
 **Папка**  
 Позволяет задать путь к отчету.  
  
 **Отчет**  
 Позволяет задать имя отчета, использующего расписание.  
  
## <a name="see-also"></a>См. также  
 [Создание, изменение и удаление расписаний](../subscriptions/create-modify-and-delete-schedules.md)   
 [Расписания](../subscriptions/schedules.md)   
 [Сервер отчетов в справке Management Studio F1](report-server-in-management-studio-f1-help.md)   
 [Соединение с сервером отчетов в Management Studio](connect-to-a-report-server-in-management-studio.md)   
 [Настройка общих свойств для диспетчер отчетов &#40;отчетов&#41;](../configure-general-properties-for-a-report-report-manager.md)  
  
  
