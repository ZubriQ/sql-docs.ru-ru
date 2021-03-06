---
title: Объект Field | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Field
helpviewer_keywords:
- Field object [ADO]
ms.assetid: b10a72fc-3c4b-4186-a70b-993dc9f7a092
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 04dbf3069896b9a7668d64a2f1d322f0b17ca5f3
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "67918686"
---
# <a name="field-object"></a>Объект Field
Представляет столбец данных с общим типом данных.  
  
## <a name="remarks"></a>Remarks  
 Каждый объект **field** соответствует столбцу в [наборе записей](../../../ado/reference/ado-api/recordset-object-ado.md). Свойство [value](../../../ado/reference/ado-api/value-property-ado.md) объектов **field** используется для задания или возврата данных для текущей записи. В зависимости от функциональных возможностей, предоставляемых поставщиком, некоторые коллекции, методы или свойства объекта **field** могут быть недоступны.  
  
 С помощью коллекций, методов и свойств объекта **field** можно выполнять следующие действия.  
  
-   Возвращает имя поля со свойством [Name](../../../ado/reference/ado-api/name-property-ado.md) .  
  
-   Просмотрите или измените данные в поле со свойством **значение** . **Значение** является свойством объекта **поля** по умолчанию.  
  
-   Возвращает основные характеристики поля с [типом](../../../ado/reference/ado-api/type-property-ado.md), [точностью](../../../ado/reference/ado-api/precision-property-ado.md)и свойствами [NumericScale](../../../ado/reference/ado-api/numericscale-property-ado.md) .  
  
-   Возвращает объявленный размер поля с помощью свойства [DefinedSize](../../../ado/reference/ado-api/definedsize-property.md) .  
  
-   Возврат фактического размера данных в заданном поле с помощью свойства [ActualSize](../../../ado/reference/ado-api/actualsize-property-ado.md) .  
  
-   Определите, какие типы функций поддерживаются для данного поля с помощью свойства [Attributes](../../../ado/reference/ado-api/attributes-property-ado.md) и коллекции [свойств](../../../ado/reference/ado-api/properties-collection-ado.md) .  
  
-   Изменяйте значения полей, содержащих длинные двоичные или длинные символьные данные с помощью методов [AppendChunk](../../../ado/reference/ado-api/appendchunk-method-ado.md) и методического [блока](../../../ado/reference/ado-api/getchunk-method-ado.md) .  
  
-   Если поставщик поддерживает пакетные обновления, устраните расхождения в значениях полей во время пакетного обновления с помощью свойств [originalValue](../../../ado/reference/ado-api/originalvalue-property-ado.md) и [UnderlyingValue](../../../ado/reference/ado-api/underlyingvalue-property.md) .  
  
 Все свойства метаданных (**имя**, **Тип**, **DefinedSize**, **точность**и **NumericScale**) доступны перед открытием **набора записей**объекта **поля** . Их установка в это время полезна для динамического создания форм.  
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства, методы и события объекта Field](../../../ado/reference/ado-api/field-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Коллекция Fields (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)   
 [Коллекция Properties (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)   
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
