---
title: Получение сведений из IHV
description: Сведения, которые необходимо получить от независимого поставщика программного обеспечения к устройству системы аналитики.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 730cf09ab7e45ea74070db591592fdb871243a77
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "74401059"
---
# <a name="information-to-obtain-from-your-ihv"></a>Сведения для получения от независимого поставщика оборудования
Когда Ваш независимый поставщик оборудования (IHV) доставляет вам новое устройство SQL Server PDW, он также доставляет сведения об оборудовании устройства и конфигурации, которые они выполнили на устройстве. Эти сведения понадобятся вам для администрирования устройства.  
  
В следующем списке приведены сведения, которые обычно требуются из вашего IHV. В некоторых случаях требуется дополнительная информация или другие сведения. Обратитесь к своему независимому поставщику оборудования, чтобы убедиться, что вся релевантная информация была передана вам при доставке устройства.  
  
|||  
|-|-|  
|**Информация или документ**|**Описание**|  
|Ведомость материалов (BOM)|В комплекте материалов перечислены компоненты, которые включены в устройство. Эти сведения необходимы для подтверждения доставки всех компонентов.<br /><br />**Важно.** Ваша ведомость материалов должна включать весовые коэффициенты для каждого из узлов устройств и для каждой полной стойки. Эта информация важна при планировании обработки и перемещения компонентов устройства, а также в том, чтобы центр обработки данных мог разместить устройство. Если в спецификации не включены веса узлов, обязательно получите эти сведения из независимого поставщика оборудования для всех узлов.|  
|Схемы кабелей|На схемах кабелей показано, как подключить сеть, питание и другие кабели для каждой стойки устройства. Эти схемы необходимы при установке устройства в центре обработки данных и в любой момент, когда необходимо удалить или заменить компонент.|  
|Требования к стойкам устройств|Перед установкой устройства в центр обработки данных необходимо знать, соответствует ли ваш центр обработки данных воздушному потоку и требованиям к длине кабелей для устройства, а также требованиям к размеру и питанию для компонентов. Дополнительные сведения о весах компонентов устройств, которые также необходимы, см. в разделе Спецификация (BOM) выше.|  
  
