---
title: Пользовательские свойства назначения "Модуль чтения данных" | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: f151c3e8-3811-457d-a3d3-6158ca65a646
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 948ebbc696048915662caaa24b791e6258c459be
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "62827615"
---
# <a name="datareader-destination-custom-properties"></a>Пользовательские свойства назначения «Модуль чтения данных»
  Назначение «Модуль чтения данных» обладает как пользовательскими свойствами, так и свойствами, общими для всех компонентов потока данных.  
  
 В следующей таблице описаны пользовательские свойства назначения «Модуль чтения данных». Все свойства, за исключением `DataReader`, доступны для чтения и записи.  
  
|Имя свойства|Тип данных|Description|  
|-------------------|---------------|-----------------|  
|DataReader|String|Имя класса назначения «Модуль чтения данных».|  
|FailOnTimeout|Логическое|Показывает, завершать ли работу с ошибкой, когда истекает время ожидания чтения (`ReadTimeout`). Это свойство имеет значение по умолчанию **False**.|  
|ReadTimeout|Целое число|Количество миллисекунд до истечения времени ожидания. По умолчанию для этого свойства устанавливается значение 30000 (30 секунд).|  
  
 Ввод и входные столбцы назначения «Модуль чтения данных» не обладают пользовательскими свойствами.  
  
 Дополнительные сведения см. в статье [DataReader Destination](datareader-destination.md).  
  
## <a name="see-also"></a>См. также:  
 [Общие свойства](../common-properties.md)  
  
  
