---
title: ISSCommandWithParameters (OLE DB) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- ISSCommandWithParameters (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- ISSCommandWithParameters interface
ms.assetid: 3419b7f3-36a3-4863-816e-e641e4e90496
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4de7c6a99afcbd7db7c6e233fb737f129b536b8b
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "63209766"
---
# <a name="isscommandwithparameters-ole-db"></a>Интерфейс ISSCommandWithParameters (OLE DB)
  Интерфейс**ISSCommandWithParameters** обеспечивает поддержку [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] XML и определяемых пользователем типов данных. Этот дополнительный интерфейс наследует основной интерфейс OLE DB, **ICommandWithParameters**. Помимо трех методов, наследуемых из интерфейса **ICommandWithParameters**( **GetParameterInfo**, **MapParameterNames**и **SetParameterInfo**), интерфейс **ISSCommandWithParameters** содержит два новых метода, которые используются для обработки серверных типов данных.  
  
> [!NOTE]  
>   Интерфейс **ISSCommandWithParameters** может использоваться при применении компонентов службы, однако сами компоненты службы этот интерфейс не используют.  
  
|Метод|Описание|  
|------------|-----------------|  
|[ISSCommandWithParameters::GetParameterProperties (OLE DB)](isscommandwithparameters-getparameterproperties-ole-db.md)|Возвращает одну структуру набора свойств **SSPARAMPROPS** в массиве для каждого определяемого пользователем типа данных или XML-параметра, переданного команде, однако для других типов параметров не возвращается ничего.|  
|[ISSCommandWithParameters::SetParameterProperties (OLE DB)](isscommandwithparameters-setparameterproperties-ole-db.md)|Задает свойства параметров для каждого параметра в отдельности по порядковому номеру либо задает свойства всех параметров сразу путем указания массива структур **SSPARAMPROPS** .|  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы &#40;OLE DB&#41;](../../database-engine/dev-guide/interfaces-ole-db.md)   
 [Использование типов данных XML](../native-client/features/using-xml-data-types.md)   
 [Использование определяемых пользователем типов данных](../native-client/features/using-user-defined-types.md)  
  
  
