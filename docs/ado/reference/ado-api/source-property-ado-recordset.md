---
title: Свойство Source (набор записей ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::putref_Source
- Recordset15::Source
- Recordset15::PutSource
- Recordset15::get_Source
- Recordset15::GetSource
- Recordset15::PutRefSource
- Recordset15::put_Source
helpviewer_keywords:
- Source property [ADO Recordset]
ms.assetid: a05ba2c9-2821-4343-8607-4de9b764ec91
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8f6ac84445272ae3657d4e25691dbbf150f32c5d
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67930923"
---
# <a name="source-property-ado-recordset"></a>Свойство Source (объект Recordset ADO)
Указывает источник данных для объекта [набора записей](../../../ado/reference/ado-api/recordset-object-ado.md) .  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает **строковое** значение или ссылку на объект [команды](../../../ado/reference/ado-api/command-object-ado.md) ; Возвращает только **строковое** значение, указывающее источник **набора записей**.  
  
## <a name="remarks"></a>Remarks  
 Используйте свойство **Source** , чтобы указать источник данных для объекта **набора записей** , используя одну из следующих команд: переменная объекта **команды** , инструкция SQL, хранимая процедура или имя таблицы.  
  
 Если задать для свойства **Source** объект **Command** , свойство [ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md) объекта **Recordset** будет наследовать значение свойства **ActiveConnection** для указанного объекта **команды** . Однако чтение свойства **Source** не приводит к возврату объекта **Command** . Вместо этого возвращается свойство [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) объекта **Command** , для которого задается **исходное** свойство.  
  
 Если свойство **Source** является инструкцией SQL, хранимой процедурой или именем таблицы, можно оптимизировать производительность, передав соответствующий аргумент *Options* вызову метода [Open](../../../ado/reference/ado-api/open-method-ado-recordset.md) .  
  
 Свойство **Source** доступно для чтения и записи закрытых объектов **Recordset** и доступно только для чтения для открытых объектов **Recordset** .  
  
## <a name="applies-to"></a>Применяется к  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также:  
 [Пример свойства Source (Visual Basic)](../../../ado/reference/ado-api/source-property-example-vb.md)   
 [Свойство Source (ошибка ADO)](../../../ado/reference/ado-api/source-property-ado-error.md)   
 [Свойство Source (объект Record ADO)](../../../ado/reference/ado-api/source-property-ado-record.md)
