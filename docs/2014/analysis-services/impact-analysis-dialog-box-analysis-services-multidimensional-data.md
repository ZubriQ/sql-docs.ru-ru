---
title: Влияет на диалоговое окно «Анализ» (службы Analysis Services — многомерные данные) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.asvs.process.impactanalysisdialog.f1
ms.assetid: 208268eb-4e14-44db-9c64-6f74b776adb6
caps.latest.revision: 19
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 02b5ee9613672762c466ba023ccabf1fa90d5892
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37299384"
---
# <a name="impact-analysis-dialog-box-analysis-services---multidimensional-data"></a>Диалоговое окно «Анализ влияния» (службы Analysis Services — многомерные данные)
  В диалоговом окне **Анализ влияния** в средах [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] и [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] можно определить и возможную обработку зависимых объектов при обработке объектов, заданных в диалоговом окне **Обработка** . Отрыть диалоговое окно **Анализ влияния** можно, нажав кнопку **Анализ влияния** в диалоговом окне **Обработка** .  
  
> [!NOTE]  
>  Объект может появляться более одного раза, если он задействован несколькими способами.  
  
## <a name="options"></a>Параметры  
 **Список объектов**  
 Выводит в сетке список зависимых объектов. Сетка содержит следующие столбцы:  
  
 **Имени объекта**  
 Выводит имя зависимого объекта, который, возможно, нужно обработать. Значок слева от имени указывает тип объекта.  
  
 **Тип**  
 Выводит тип зависимого объекта, который, возможно, нужно обработать.  
  
 **Тип воздействия**  
 Отображает эффект, который обработка объектов в диалоговом окне **Обработка** оказывает на данный зависимый объект. Следующая таблица содержит список возможных эффектов от обработки и примечания, приводит ли это к предупреждению или ошибке.  
  
|Воздействие|Сообщение|  
|------------|-------------|  
|Объект будет очищен (не обработан).|Предупреждение|  
|Объект может быть недопустимым.|Ошибка|  
|Статистическая функция будет удалена.|Предупреждение|  
|Гибкая статистическая функция будет удалена.|Предупреждение|  
|Индексы будут удалены.|Предупреждение|  
|Объект, не являющийся потомком, будет обработан.|Предупреждение|  
  
 **Объект процесса**  
 Выберите зависимые объекты, которые нужно обработать в данной операции обработки. Невыбранные зависимые объекты должны быть обработаны после завершения операции обработки. В противном случае их нельзя будет использовать.  
  
## <a name="see-also"></a>См. также  
 [Конструкторы и диалоговые окна служб Analysis Services &#40;многомерных данных&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Диалоговое окно обработки &#40;службы Analysis Services — многомерные данные&#41;](process-dialog-box-analysis-services-multidimensional-data.md)  
  
  