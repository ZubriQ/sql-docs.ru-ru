---
title: Добавление представления источников данных для прогнозирования (учебник по интеллектуальному анализу данных — средний уровень) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 2665040a-1291-4064-ba01-f458637dda57
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: f60ea2b2a642cf9435ed8366c42e43abb927e426
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "62823134"
---
# <a name="adding-a-data-source-view-for-forecasting-intermediate-data-mining-tutorial"></a>Добавление представления источников данных для прогнозирования (учебник по интеллектуальному анализу данных — средний уровень)
  В этой задаче добавляется новое представление источника данных, которое будет использоваться в сценарии прогнозирования. Модель прогнозирования требует, чтобы данные содержали столбец, который может быть использован для идентификации шагов временных рядов. Если планируется анализировать несколько рядов данных, то все ряды должны заканчиваться на одном и том же шаге даты или времени.  
  
### <a name="to-add-a-data-source-view"></a>Добавление представления источников данных  
  
1.  В обозреватель решений щелкните правой кнопкой мыши элемент **представления источников данных**и выберите пункт **создать представление источника данных**.  
  
2.  На странице **Мастер представления источника данных** нажмите кнопку **Далее**.  
  
3.  На странице **Выбор источника данных** в разделе **реляционные источники данных**выберите источник [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] данных. Нажмите кнопку **Далее**.  
  
    > [!NOTE]  
    >  Если этот источник данных отсутствует, шаги по созданию источника данных можно найти в [учебнике по основам интеллектуального анализа данных](../../2014/tutorials/basic-data-mining-tutorial.md).  
  
4.  На странице **Выбор таблиц и представлений** выберите таблицу vTimeSeries (dbo), а затем щелкните стрелку вправо, чтобы добавить ее в представление источника данных.  
  
5.  Нажмите кнопку **Далее**.  
  
6.  На странице **Завершение работы мастера** по умолчанию представление источника данных имеет имя [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)]. Измените имя на **SalesByRegion**и нажмите кнопку **Готово**.  
  
     Откроется конструктор представлений источников данных, и появится представление источника данных **SalesByRegion** .  
  
## <a name="working-with-the-data-source-view"></a>Работа с представлением источника данных  
 После создания представления источников данных можно исследовать данные приведенными ниже способами.  
  
-   Щелкните правой кнопкой мыши таблицу vTimeSeries в конструкторе и выберите **Просмотр данных** , чтобы открыть выбранную таблицу в сетке.  
  
-   Щелкните **Параметры выборки** , а затем используйте диалоговое окно **Параметры просмотра данных** , чтобы изменить метод выборки. Нажмите кнопку **Обновить** , чтобы загрузить данные в таблицу с помощью параметров новый параметр. Например, можно указать количество строк для вывода в выборке или выбрать n верхних строк.  
  
-   Щелкните правой кнопкой мыши таблицу vTimeSeries и выберите **Свойства** , чтобы назначить таблице новое имя. Также можно выбрать отдельные столбцы в представлении источников данных и изменить свойства столбца.  
  
-   Щелкните любой участок области конструктора представления источников данных, создайте новый запрос и задайте имя для него, чтобы создать связи между таблицами, либо измените макет в области конструктора.  
  
-   Щелкните правой кнопкой мыши таблицу и выберите **Создать именованное вычисление** , чтобы создать производные столбцы, включая агрегаты. Можно также добавить в это представление новые таблицы и представления из источника данных.  
  
 В следующей задаче рассмотрим некоторые временные ряды данных и определим, какой столбец лучше всего использовать в качестве идентификатора временных рядов. Вы также узнаете, как обрабатывать промежутки данных во временных рядах.  
  
## <a name="next-task-in-lesson"></a>Следующая задача занятия  
 [Основные сведения о требованиях к модели временных рядов &#40;руководстве по интеллектуальному анализу данных&#41;](../../2014/tutorials/time-series-model-requirements-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>См. также  
 [Алгоритм временных рядов (Майкрософт)](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md)  
  
  
