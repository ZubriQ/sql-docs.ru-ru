---
title: dbo. систаскидс (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- systaskids_TSQL
- dbo.systaskids
- systaskids
- dbo.systaskids_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- systaskids system table
ms.assetid: 45c56d89-4160-4d84-80bf-a7a05488792d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9ed9ac8e81abaf6367d3a9c5518f1f18cb94ef8b
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67990399"
---
# <a name="dbosystaskids-transact-sql"></a>dbo.systaskids (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит сопоставление задач, созданных в более ранних версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], с заданиями среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] текущей версии. Эта таблица хранится в базе данных **msdb** .  
  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**task_id**|**int**|Идентификатор задачи.|  
|**job_id**|**uniqueidentifier**|Идентификатор задания, с которым сопоставляется задача.|  
  
  
