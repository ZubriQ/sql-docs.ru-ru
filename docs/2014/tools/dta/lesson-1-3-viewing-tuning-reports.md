---
title: Просмотр отчетов по настройке | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- tuning reports [SQL Server]
ms.assetid: daee6143-269f-428b-8458-9a3e726d586c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4963a309f6c54998ece968f8a5393e818fd30d07
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66110144"
---
# <a name="viewing-tuning-reports"></a>Просмотр отчетов настройки
  В предыдущей практической работе этого учебника были рассмотрены скрипты [!INCLUDE[tsql](../../includes/tsql-md.md)] , которые создают или сбрасывают объекты базы данных в рекомендациях помощника по настройке ядра СУБД, которые были созданы в сеансе настройки MySession. Сеанс настройки MySession был создан в разделе [Tuning a Workload](lesson-1-1-tuning-a-workload.md).  
  
 Хотя очень полезно рассмотреть скрипты, которые можно использовать для применения результатов настройки, помощник по настройке ядра СУБД также предоставляет много полезных отчетов. Эти отчеты содержат сведения о существующих структурах физического проектирования в настраиваемой базе данных, а также о рекомендуемых структурах. Отчеты настройки можно просмотреть, перейдя на вкладку **Отчеты** , как описано в следующей практической работе. В этой практической работе используются сеансы настройки MySession и EvaluateMySession, которые были созданы упражнениях разделов [Tuning a Workload](lesson-1-1-tuning-a-workload.md) и [Viewing Tuning Recommendations](lesson-1-2-viewing-tuning-recommendations.md).  
  
### <a name="view-tuning-reports"></a>Просмотр отчетов настройки  
  
1.  Запустите помощник по настройке ядра СУБД. См. раздел [Запуск помощника по настройке ядра СУБД](../../relational-databases/performance/database-engine-tuning-advisor.md). Убедитесь, что установлено подключение к тому же экземпляру служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , который был использован во время предыдущих практических работ этого занятия.  
  
     Дважды щелкните сеанс **MySession** на панели **Монитор сеансов** . Помощник по настройке ядра СУБД загрузит сведения о сеансе из этого сеанса.  
  
2.  Перейдите на вкладку **Отчеты** .  
  
3.  На панели **Сводка по настройке** можно просмотреть сведения об этом сеансе настройки. Используйте полосу прокрутки, чтобы просмотреть содержимое панели полностью. Обратите внимание на поля **Ожидаемый процент улучшений** и **Пространство, занятое рекомендацией**. При настройке можно ограничить место для рекомендаций. На вкладке **Параметры настройки** выберите **Дополнительные параметры**. Установите флажок **Задавать макс. пространство для рекомендаций** и укажите в мегабайтах максимальное пространство, которое может использовать конфигурация рекомендаций. Для возврата в этот учебник нажмите кнопку **Назад** в окне справки.  
  
4.  На панели **Отчеты о настройке** щелкните **Отчет о стоимости инструкций** в списке **Выбор отчета** . Если необходимо больше места для просмотра отчета, перетащите границу панели **Монитор сеансов** влево. У каждой инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] , применяемой к таблице базы данных, есть своя стоимость применения. Эта стоимость может быть уменьшена путем создания эффективных индексов для часто используемых столбцов таблицы. Данный отчет показывает предполагаемую степень улучшения при выполнении рекомендации по настройке по сравнению с исходной стоимостью выполнения инструкции. Обратите внимание, что количество данных, содержащихся в отчете, основано на размере и сложности рабочей нагрузки.  
  
5.  Щелкните правой кнопкой мыши панель **Отчет о стоимости инструкций** в области сетки и выберите команду **Экспорт в файл**. Сохраните отчет как `MyReport`. К имени файла будет автоматически добавлено расширение XML. Файл MyReport.xml можно открыть в любом XML-редакторе или в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , чтобы просмотреть содержимое отчета.  
  
6.  Вернитесь на вкладку **Отчеты** помощника по настройке ядра СУБД и снова щелкните правой кнопкой мыши область **Отчет о стоимости инструкций** . Просмотрите другие доступные параметры. Обратите внимание, что можно менять шрифт просматриваемого отчета. Изменение шрифта повлияет и на другие страницы с вкладками.  
  
7.  Щелкните другие отчеты в списке **Выбор отчета** , чтобы ознакомиться с ними.  
  
## <a name="summary"></a>Сводка  
 Изучена вкладка **Отчеты** графического интерфейса помощника по настройке ядра СУБД для сеанса настройки MySession. Выполните эти шаги, чтобы ознакомиться с отчетами, созданными для сеанса настройки EvaluateMySession. Дважды щелкните сеанс **EvaluateMySession** на панели **Монитор сеансов** .  
  
## <a name="next-lesson"></a>Следующее занятие  
 [Урок 3. Использование программы командной строки dta](lesson-3-using-the-dta-command-prompt-utility.md)  
  
  
