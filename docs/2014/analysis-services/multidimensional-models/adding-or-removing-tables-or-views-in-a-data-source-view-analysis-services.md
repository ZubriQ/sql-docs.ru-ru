---
title: Добавление или удаление таблиц или представлений в данных источника (службы Analysis Services) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dsvdesigner.tablespane.f1
helpviewer_keywords:
- deleting tables
- tables [Analysis Services]
- removing tables
- adding tables
- data source views [Analysis Services], tables
- tables [Analysis Services], data source views
ms.assetid: 98307d04-6548-4d7d-9244-2371dd165249
caps.latest.revision: 34
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0ac190f75b626cf2007dee5c885c45672276ee35
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37179071"
---
# <a name="adding-or-removing-tables-or-views-in-a-data-source-view-analysis-services"></a>Добавление или удаление таблиц или представлений в представлении источника данных (службы Analysis Services)
  После создания представления источников данных (DSV) в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]можно изменить его в конструкторе представлений источников данных, добавляя или удаляя таблицы и столбцы, в том числе из других источников данных.  
  
 Чтобы открыть представление источника данных (DSV) в конструкторе представлений источников данных, дважды щелкните DSV в обозревателе решений. После открытия представления источников данных для его изменения или расширения можно использовать команду **Добавить или удалить таблицы** на панели кнопок или в меню. Также можно использовать объекты диаграммы. Например, можно выбрать объект и нажать клавишу «Delete» на клавиатуре для удаления объекта.  
  
> [!WARNING]  
>  Будьте внимательны при удалении таблицы. При удалении таблицы удаляются все соответствующие столбцы и связи из представления источников данных (DSV), а все объекты, связанные с таблицей, становятся недействительными.  
  
## <a name="selecting-tables-or-views-to-add-or-remove"></a>Выбор таблиц и представлений для добавления или удаления  
 С помощью диалогового окна **Добавление или удаление таблиц** можно перемещать таблицы или представления между списками **Доступные объекты** и **Включенные объекты** . Список **Доступные объекты** изначально включает все таблицы или представления в первичном источнике данных, которые пока не включены в представление источника данных. Если первичный источник данных поддерживает `OPENROWSET` функцию, можно также добавить таблицы или представления из других источников данных в проекте или базе данных.  
  
 При добавлении или удалении таблицы из представление источника данных (DSV) осуществляется добавление или удаление таблицы в текущую выбранную диаграмму в DSV. Дополнительные сведения о диаграммах см. в разделе [Work with Diagrams in Data Source View Designer &#40;Analysis Services&#41;](work-with-diagrams-in-data-source-view-designer-analysis-services.md).  
  
 После перемещения таблицы в список **Включенные объекты** в диалоговом окне **Добавление или удаление таблиц** можно добавить все связанные таблицы. При этой операции таблицы добавляются в соответствии с ограничениями внешних ключей в источнике данных, если такие ограничения существуют. Если ограничения внешнего ключа не существует, можно использовать `NameMatchingCriteria` свойства представления источников данных для определения связей, указывая критерий для сопоставления имен столбцов в таблицах для формирования вероятных связей. Если `NameMatchingCriteria`для представления источников данных задано свойство, нажмите кнопку **добавить связанные таблицы** для добавления таблиц из источника данных, имеющих совпадающие имена столбцов. Дополнительные сведения о параметре `NameMatchingCriteria` свойство, см. в разделе [представления источников данных в многомерных моделях](data-source-views-in-multidimensional-models.md).  
  
> [!NOTE]  
>  Добавление или удаление объектов в представлении источника данных не влияет на базовый источник данных.  
  
## <a name="see-also"></a>См. также  
 [Представления источников данных в многомерных моделях](data-source-views-in-multidimensional-models.md)   
 [Работа с диаграммами в конструкторе представлений источников данных &#40;служб Analysis Services&#41;](work-with-diagrams-in-data-source-view-designer-analysis-services.md)  
  
  