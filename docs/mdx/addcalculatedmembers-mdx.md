---
title: AddCalculatedMembers (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 982484b729b59a7106b6195e361110c1d4012653
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68017182"
---
# <a name="addcalculatedmembers-mdx"></a>AddCalculatedMembers (многомерные выражения)


  Возвращает набор, созданный путем добавления вычисляемых элементов в указанный набор.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
AddCalculatedMembers(Set_Expression)   
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Expression*  
 Допустимое многомерное выражение, возвращающее набор.  
  
## <a name="remarks"></a>Remarks  
 По умолчанию в языке многомерных выражений вычисляемые элементы исключаются при вычислении функций набора. Функция **AddCalculatedMembers** проверяет выражение набора, указанное в *Set_Expression,* и включает вычисляемые элементы, которые являются одноуровневыми элементами, содержащимися в области этого выражения набора.  
  
> [!NOTE]  
>  Эту функцию можно использовать только для одномерных выражений наборов.  
  
## <a name="examples"></a>Примеры  
 В следующем примере показано использование этой функции.  
  
```  
-- This query returns the calculated members for the cube  
-- by retrieving all members, and then excluding non-calculated members.  
SELECT   
   AddCalculatedMembers(  
      {[Measures].Members}  
      )-[Measures].Members ON COLUMNS  
FROM [Adventure Works]   
```  
  
 В следующем примере возвращается `Measures.[Unit Price]` элемент в дополнение ко всем вычисляемым элементам в измерении **Measures** из куба **Adventure Works** .  
  
```  
SELECT  
   AddCalculatedMembers({Measures.[Unit Price]}) ON COLUMNS  
FROM   
   [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
