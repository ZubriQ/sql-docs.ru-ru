---
title: Локктипинум | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- LockTypeEnum
helpviewer_keywords:
- LockTypeEnum enumeration [ADO]
ms.assetid: d2894eaf-4450-4ace-aa51-c8b875fd3010
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0ae822794b1b06a975e1cc3cd397b5a5f00036dc
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "67918249"
---
# <a name="locktypeenum"></a>LockTypeEnum
Указывает тип блокировки, помещаемой в записи во время редактирования.  
  
|Константа|Применение|Описание|  
|--------------|-----------|-----------------|  
|**адлоккбатчоптимистик**|4|Обозначает обновления оптимистических пакетов. Требуется для режима пакетного обновления.|  
|**adLockOptimistic**|3|Обозначает оптимистичную блокировку, запись по записям. Поставщик использует оптимистичную блокировку, блокируя записи только при вызове метода [Update](../../../ado/reference/ado-api/update-method.md) .|  
|**адлоккпессимистик**|2|Указывает пессимистическую блокировку, запись по записям. Поставщик выполняет необходимые действия, чтобы обеспечить успешное редактирование записей, обычно путем блокировки записей в источнике данных сразу после редактирования.|  
|**адлоккреадонли**|1|Указывает записи, которые доступны только для чтения. Изменить данные нельзя.|  
|**адлоккунспеЦифиед**|-1|Не указывает тип блокировки. Для клонов создается клон с тем же типом блокировки, что и у оригинала.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Пакет: **com. MS. WFC. Data**  
  
|Константа|  
|--------------|  
|Адоенумс. LockType. БАТЧОПТИМИСТИК|  
|Адоенумс. LockType. ОПТИМИСТИЧный|  
|Адоенумс. LockType. ПЕССИМИСТическая|  
|Адоенумс. LockType. READONLY|  
|Адоенумс. LockType. не указано|  
  
## <a name="applies-to"></a>Применяется к  
  
|||  
|-|-|  
|[Метод Clone (ADO)](../../../ado/reference/ado-api/clone-method-ado.md)|[Свойство LockType (ADO)](../../../ado/reference/ado-api/locktype-property-ado.md)|  
|[Метод Open (объект Recordset ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md)|[Событие WillExecute (ADO)](../../../ado/reference/ado-api/willexecute-event-ado.md)|
