---
title: Получение дескрипторов дескрипторов | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- descriptors [ODBC], retrieving or setting field values
ms.assetid: 936f983f-c7e9-43f3-97ea-dd4b1bbf4654
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c17b693080c2727d2ee788b74f247d86d7a3cb27
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81302349"
---
# <a name="obtaining-descriptor-handles"></a>Получение указателей дескрипторов
Приложение получает дескриптор любого явно выделенного дескриптора в качестве выходного аргумента для вызова **функцию SQLAllocHandle**. Дескриптор неявно выделенного дескриптора получается путем вызова **SQLGetStmtAttr**.
