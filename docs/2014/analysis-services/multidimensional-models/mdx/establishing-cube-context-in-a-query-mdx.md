---
title: Установка контекста куба в запросе (многомерные выражения) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- cubes [Analysis Services], MDX
- MDX [Analysis Services], cube context
- SELECT statement [MDX]
- Multidimensional Expressions [Analysis Services], cube context
- queries [MDX], cube context
ms.assetid: 79d6a1e8-2825-4eb9-97df-5071aecae8f0
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f9f0f960c531fac8bae8f03479bacd507ffc3078
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66074603"
---
# <a name="establishing-cube-context-in-a-query-mdx"></a>Определение контекста куба в запросе (многомерные выражения)
  Каждый запрос многомерных выражений выполняется в заданном контексте куба. Контекст определяет элементы, вычисляемые в выражениях запроса.  
  
 В инструкции SELECT контекст куба определяется с помощью предложения FROM. В качестве контекста может выступать весь куб или его вложенный куб. Указав контекст куба при помощи предложения FROM, можно расширять или ограничивать его при помощи дополнительных функций.  
  
> [!NOTE]  
>  Инструкции SCOPE и CALCULATE также позволяют управлять контекстом куба в скрипте многомерных выражений. Дополнительные сведения см. в статье [Основные принципы создания скриптов многомерных выражений (службы Analysis Services)](mdx-scripting-fundamentals-analysis-services.md).  
  
## <a name="from-clause-syntax"></a>Синтаксис предложения FROM  
 Предложение FROM имеет следующий синтаксис.  
  
```  
<SELECT subcube clause> ::=  
   Cube_Identifier |   
   (SELECT [  
      * |   
      ( <SELECT query axis clause> [ , <SELECT query axis clause> ... ] ) ]   
   FROM <SELECT subcube clause> <SELECT slicer axis clause> )  
```  
  
 Обратите внимание на то, что в этом синтаксисе куб или вложенный куб, над которым выполняется инструкция SELECT, описывается предложением `<SELECT subcube clause>` .  
  
 Простым примером использования предложения FROM является запрос, обрабатывающий весь образец куба Adventure Works. Предложение FROM будет иметь следующий вид:  
  
```  
FROM [Adventure Works]  
```  
  
 Дополнительные сведения о предложении FROM в инструкции SELECT многомерных выражений см. в разделе [Инструкция SELECT (многомерные выражения)](/sql/mdx/mdx-data-manipulation-select).  
  
## <a name="refining-the-context"></a>Уточнение контекста  
 Хотя в предложении FROM контекст задается внутри одного куба, это не запрещает одновременно работать с данными из нескольких кубов.  
  
 Для получения данных из кубов, которые не входят в заданный контекст куба, применяется функция многомерных выражений [LookupCube](/sql/mdx/lookupcube-mdx) . Кроме того, для временного сужения контекста при вычислении запроса можно использовать такие функции как [Filter](/sql/mdx/filter-mdx) .  
  
## <a name="see-also"></a>См. также  
 [Основные принципы запросов многомерных выражений (службы Analysis Services)](mdx-query-fundamentals-analysis-services.md)  
  
  
