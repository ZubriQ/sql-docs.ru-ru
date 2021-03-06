---
title: Руководство по RDS | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS tutorial [ADO]
ms.assetid: 6e3305a0-7bc7-40d1-9122-235c15d23ab2
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 541c92cd34b9cbaecdd1001be29dbab8d9b194a0
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67922410"
---
# <a name="rds-tutorial"></a>Учебник по RDS
В этом учебнике показано, как использовать модель программирования RDS для запроса и обновления источника данных. Во первых, он описывает шаги, необходимые для выполнения этой задачи. Затем этот учебник повторяется в Microsoft® Visual Basic Scripting Edition (в котором используется ADO для классов Windows Foundation (ADO/WFC)).  
  
 Этот учебник написан на разных языках по двум причинам:  
  
-   В документации по RDS предполагается, что коды модуля чтения находятся в Visual Basic. Это делает документацию удобной для Visual Basic программистов, но менее полезна для программистов, использующих другие языки.  
  
-   Если вы не уверены в конкретном компоненте RDS и вам известно о некоторых других языках, вы можете разрешить свой вопрос, выполнив поиск той же функции, которая представлена на другом языке.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, компоненты RDS больше не включены в операционную систему Windows (Дополнительные сведения см. в статье о совместимости Windows 8 и [Windows server 2012 Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). Клиентские компоненты RDS будут удалены в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие RDS, должны переноситься в [службу данных WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="how-the-tutorial-is-presented"></a>Как представлен учебник  
 Этот учебник основан на модели программирования RDS. В нем обсуждается каждый шаг модели программирования по отдельности. Кроме того, он иллюстрирует каждый шаг с фрагментом кода Visual Basic.  
  
 Пример кода повторяется на других языках с минимальным обсуждением. Каждый шаг в данном руководстве по языку программирования помечается соответствующим шагом в модели программирования и описательном руководстве. Используйте номер шага для ссылки на обсуждение в учебнике.  
  
 Модель программирования RDS указывается в следующем разделе. Используйте его в качестве плана при продолжении работы с руководством.  
  
## <a name="rds-programming-model-with-objects"></a>Модель программирования RDS с объектами  
  
-   Укажите программу, которая будет вызываться на сервере, и получите способ (прокси) для ссылки на него из клиента.  
  
-   Вызов серверной программы. Передайте в серверную программу параметры, определяющие источник данных, и выдаваемый командой.  
  
-   Серверная программа получает объект [набора записей](../../../ado/reference/ado-api/recordset-object-ado.md) из источника данных, обычно с помощью ADO. При необходимости объект **набора записей** обрабатывается на сервере.  
  
-   Серверная программа возвращает последний объект **набора записей** в клиентское приложение.  
  
-   На клиенте объект **Recordset** дополнительно может быть размещен в форме, которую можно легко использовать в визуальных элементах управления.  
  
-   Изменения объекта **набора записей** отправляются обратно на сервер и используются для обновления источника данных.  
  
 Этот учебник содержит следующие разделы.  
  
-   [Шаг 1. Укажите программу сервера (учебник по RDS)](../../../ado/guide/remote-data-service/step-1-specify-a-server-program-rds-tutorial.md)  
  
-   [Шаг 2. Вызовите программу сервера (учебник по RDS)](../../../ado/guide/remote-data-service/step-2-invoke-the-server-program-rds-tutorial.md)  
  
-   [Шаг 3. Сервер получает набор записей (учебник по RDS)](../../../ado/guide/remote-data-service/step-3-server-obtains-a-recordset-rds-tutorial.md)  
  
-   [Шаг 4. Сервер возвращает набор записей (учебник по RDS)](../../../ado/guide/remote-data-service/step-4-server-returns-the-recordset-rds-tutorial.md)  
  
-   [Шаг 5. DataControl теперь можно использовать (учебник по RDS)](../../../ado/guide/remote-data-service/step-5-datacontrol-is-made-usable-rds-tutorial.md)  
  
-   [Шаг 6. Изменения отправлены на сервер (учебник по RDS)](../../../ado/guide/remote-data-service/step-6-changes-are-sent-to-the-server-rds-tutorial.md)  
  
-   [Учебник по RDS (VBScript)](../../../ado/guide/remote-data-service/rds-tutorial-vbscript.md)  
  
## <a name="see-also"></a>См. также:  
 [Шаг 1. Указание серверной программы (учебник по RDS)](../../../ado/guide/remote-data-service/step-1-specify-a-server-program-rds-tutorial.md)   
 [Учебник по RDS (VBScript)](../../../ado/guide/remote-data-service/rds-tutorial-vbscript.md)   
