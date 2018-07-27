---
title: Просмотр данных в представлении источника данных (службы Analysis Services) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- exploring data [Analysis Services]
- data source views [Analysis Services], exploring data
- viewing source data
ms.assetid: 2c922c35-fbcb-45b2-96b1-c7a846d8b419
caps.latest.revision: 32
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 22d8f26a22f2cda64a6a9999ce4a2a730e4e5c06
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37183467"
---
# <a name="explore-data-in-a-data-source-view-analysis-services"></a>Просмотр данных в представлении источника данных (службы Analysis Services)
  Диалоговое окно **Просмотр данных** конструктора представлений источников данных в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] служит для просмотра данных таблицы, представления или именованного запроса в представлении источника данных. При просмотре данных в конструкторе представлений источника данных можно видеть содержимое каждого столбца данных в выбранной таблице, представлении или именованном запросе. Просмотр содержимого помогает определить, все ли столбцы нужны (если именованные вычисления требуются для повышения удобства для пользователя) и возвращают ли существующие именованные вычисления и именованные запросы ожидаемые результаты.  
  
 Для просмотра данных требуется активное соединение с источником или источниками данных выбранного объекта в представлении источника данных. Любые именованные вычисления в таблице также передаются в запрос.  
  
 Данные возвращаются в табличном формате, поддерживающем сортировку и копирование. Чтобы пересортировать строки по некоторому столбцу, щелкните его заголовок. Также можно выделить данные в сетки и нажать клавиши CTRL-C, чтобы скопировать их в буфер обмена.  
  
 Также можно менять метод выборки и размер выборки. По умолчанию возвращаются первые 5000 строк.  
  
## <a name="to-browse-data-or-change-sampling-options"></a>Просмотр данных или изменение параметров выборки  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]откройте проект или подключитесь к базе данных, содержащей представление источника данных, в котором нужно просмотреть данные.  
  
2.  В обозревателе решений откройте папку **Представления источников данных** , а затем дважды щелкните представление источника данных.  
  
3.  Щелкните правой кнопкой мыши таблицу, представление или именованный запрос, содержащие данные, которые необходимо просмотреть, а затем выберите пункт **Просмотр данных**.  
  
     Данные источника, основной таблицы, представления или именованного запроса в представлении источника данных являются запросы, а результаты отображаются в **Проводник \<имя объекта > таблицы** вкладки.  
  
4.  На **Проводник \<имя объекта > таблицы** панели инструментов нажмите кнопку **параметры выборки** значок.  
  
     Откроется диалоговое окно **Параметры просмотра данных** . В этом диалоговом окне можно задать метод выборки (уменьшив или увеличив количество записей выборки, по умолчанию равное 5000 строк) или размер выборки.  
  
5.  Нажмите кнопку **ОК** или **Отмена** .  
  
6.  Для повторной выборки данных, щелкните **Повторить выборку данных** на **Проводник \<имя объекта > таблицы** панели инструментов.  
  
## <a name="see-also"></a>См. также  
 [Представления источников данных в многомерных моделях](data-source-views-in-multidimensional-models.md)  
  
  