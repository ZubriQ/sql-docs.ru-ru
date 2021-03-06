---
title: Секции табличной модели (табличные службы SSAS) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.ssms.partitions.partitionmgr.imbi.f1
ms.assetid: 041c269f-a229-4a41-8794-6ba4b014ef83
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: aaa2b608665e50b25b39d78a39a57bb08b55cf31
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66066384"
---
# <a name="tabular-model-partitions-ssas-tabular"></a>Секции табличных моделей (табличные службы SSAS)
  Секции разделяют таблицу на логические части. Каждая секция затем может обрабатываться (обновляться) независимо от других секций. Секции, определенные для модели во время разработки модели, дублируются в модели развертывания. После развертывания можно настроить управление секциями и создавать новые секции с помощью диалогового окна **Секции** в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или с помощью скрипта. В этом разделе описываются секции в развернутой табличной модели базы данных. Дополнительные сведения о создании и управлении секциями во время разработки модели см. в разделе [Секции (табличные службы SSAS)](partitions-ssas-tabular.md).  
  
 Разделы данной темы:  
  
-   [Преимущества](#bkmk_benefits)  
  
-   [Разрешения](#bkmk_permissions)  
  
-   [Обработка секций](#bkmk_process_partitions)  
  
-   [Связанные задачи](#bkmk_related_tasks)  
  
##  <a name="benefits"></a><a name="bkmk_benefits"></a>Среди  
 При эффективной разработке моделей секции используются для устранения ненужной обработки и последующей нагрузки на процессор на серверах служб Analysis Services. При этом одновременно гарантируется обработка этих данных и частота обновления, достаточная для отражения последних данных из источников данных.  
  
 Например, табличная модель может содержать таблицу Sales, содержащую данные продаж за текущий финансовый год (2011 г.) и за все предыдущие финансовые годы. Таблица Sales (продажи) модели имеет следующие три секции:  
  
|Секция|Данные из|  
|---------------|---------------|  
|Sales2011|Текущий финансовый год|  
|Sales2010-2001|Финансовые годы 2001, 2002, 2003, 2004, 2005, 2006. 2007, 2008, 2009, 2010|  
|SalesOld|Все финансовые годы перед последними десятью финансовыми годами.|  
  
 По мере добавления новых данных продаж для текущего финансового 2011 года эти данные необходимо обработать для точного отражения в анализе данных продаж за текущий финансовый год, таким образом, секция Sales2011 обрабатывается в ночное время.  
  
 Нет необходимости в обработке данных в секции Sales2010-2001 в ночное время. Однако, поскольку данные продаж за предыдущие десять финансовых лет периодически могут изменяться из-за возврата продуктов и других изменений, они должны обрабатываться регулярно. Поэтому данные в секции Sales2010-2001 обрабатываются ежемесячно. Данные в секции SalesOld никогда не изменяются, поэтому эта секция обрабатывается только один раз в год.  
  
 При вводе финансового года 2012 в таблицу Sales (продажи) в режиме добавляется новая секция секция Sales2012. Затем секцию Sales2011 можно объединить с секцией Sales2010-2001 и переименовать новую секцию в Sales2011-2002. Данные за финансовый год 2001 удаляются из секции Sales2011-2002 и перемещаются в секцию SalesOld. Затем все секции обрабатываются для отражения изменений.  
  
 Реализация стратегии секционирования для табличных моделей организации во многом зависит от потребностей конкретной модели обработки данных и доступных ресурсов.  
  
##  <a name="permissions"></a><a name="bkmk_permissions"></a> Permissions  
 Для создания, обработки и управления секциями в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]необходимы соответствующие разрешения служб Analysis Services, определенные в роли безопасности. Каждая роль безопасности имеет одно из следующих разрешений.  
  
|Разрешение|Действия|  
|----------------|-------------|  
|Администратор|Чтение, обработка, создание, копирование, слияние, удаление|  
|Процесс|Чтение, обработка|  
|Только для чтения|Чтение|  
  
 Дополнительные сведения о создании ролей при создании моделей с помощью [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] см. в разделе [Роли (табличные службы SSAS)](roles-ssas-tabular.md). Дополнительные сведения об управлении членами ролей для развернутых табличных моделей с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] см. в разделе [Роли табличных моделей (табличные службы SSAS)](tabular-model-roles-ssas-tabular.md).  
  
##  <a name="process-partitions"></a><a name="bkmk_process_partitions"></a>Обработка секций  
 Секции можно обработать (обновить) независимо от других секций с помощью диалогового окна **Секции** в [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] или с помощью скрипта. Для обработки можно задать следующие параметры:  
  
|Режим|Описание|  
|----------|-----------------|  
|Обработка. По умолчанию|Обнаруживает состояние обработки объекта секции и выполняет обработку, необходимую для перевода необработанных или частично обработанных объектов секции в полностью обработанное состояние. Выполняется загрузка данных для пустых таблиц и секций; иерархии, вычисляемые столбцы и связи строятся или перестраиваются.|  
|Обработка. Полная|Обрабатывает объект секций и все объекты, которые в нем содержатся. Если объект, который обрабатывается методом полной обработки, уже был обработан, службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] удаляют все данные объекта, а затем обрабатывают его. Этот тип обработки требуется при внесении структурных изменений в объект.|  
|Обработка данных|Выполняется загрузка данных в секцию или таблицу без перестроения иерархий или связей или повторного вычисления вычисленных столбцов и мер.|  
|Обработка с очисткой|Удаляет все данные из секции.|  
|Обработка с добавлением|Постепенно обновляет секцию с включением новых данных.|  
  
##  <a name="related-tasks"></a><a name="bkmk_related_tasks"></a> Связанные задачи  
  
|Задача|Описание|  
|----------|-----------------|  
|[Создание секций табличной модели и управление ими (табличные службы SSAS)](create-and-manage-tabular-model-partitions-ssas-tabular.md)|Содержит описание обработки секций и управления ими в развернутых табличных моделях в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].|  
|[Обработка секций табличной модели (табличные службы SSAS)](process-tabular-model-partitions-ssas-tabular.md)|Содержит описание обработки секций в развернутых табличных моделях с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].|  
  
  
