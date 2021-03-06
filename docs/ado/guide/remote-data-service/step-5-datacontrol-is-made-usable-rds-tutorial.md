---
title: Шаг 5. Использование элемента управления "Управление доступом" (руководство по RDS) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS tutorial [ADO], datacontrol made usable
ms.assetid: ed5c4a24-9804-4c85-817e-317652acb9b4
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1202a25c603b5dd4f9a824b031b5af91f5940052
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67922056"
---
# <a name="step-5-datacontrol-is-made-usable-rds-tutorial"></a>Шаг 5. DataControl теперь можно использовать (учебник по RDS)
Возвращаемый объект **набора записей** доступен для использования. Вы можете просматривать, перемещать или изменять его так же, как любой другой **набор записей**. Действия, которые можно выполнять с **набором записей** , зависят от среды. Visual Basic и Visual C++ имеют визуальные элементы управления, которые могут напрямую или косвенно использовать **набор записей** с помощью включения элемента управления данными.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, компоненты RDS больше не включены в операционную систему Windows (Дополнительные сведения см. в статье о совместимости Windows 8 и [Windows server 2012 Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). Клиентские компоненты RDS будут удалены в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие RDS, должны переноситься в [службу данных WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Например, при отображении веб-страницы в Microsoft Internet Explorer может потребоваться отобразить данные объекта **набора записей** в визуальном элементе управления. Визуальные элементы управления на веб-странице не могут напрямую обращаться к объекту **Recordset** . Однако они могут получить доступ к объекту **Recordset** через [RDS. Элемент управления](../../../ado/reference/rds-api/datacontrol-object-rds.md). **RDS. Элемент управления** данных может использоваться визуальным элементом управления, если его свойство [саурцерекордсет](../../../ado/reference/rds-api/recordset-sourcerecordset-properties-rds.md) имеет значение Object **Recordset** .  
  
 Для объекта визуального элемента управления параметр **DATASRC** должен иметь значение **RDS. Элемент управления**данных и его свойство **DATAFLD** , установленное в поле объекта **набора записей** (столбец).  
  
 В этом руководстве задайте свойство **саурцерекордсет** :  
  
```vb
Sub RDSTutorial5()  
   Dim DS as New RDS.DataSpace  
   Dim RS as ADODB.Recordset  
   Dim DC as New RDS.DataControl  
   Dim DF as Object  
   Set DF = DS.CreateObject("RDSServer.DataFactory", "https://yourServer")  
   Set RS = DF.Query ("DSN=Pubs", "SELECT * FROM Authors")  
   DC.SourceRecordset = RS         ' Visual controls can now bind to DC.  
...  
```  
  
## <a name="see-also"></a>См. также:  
 [Шаг 6. изменения, отправляемые на сервер (учебник по RDS)](../../../ado/guide/remote-data-service/step-6-changes-are-sent-to-the-server-rds-tutorial.md)   
 [Учебник по RDS (VBScript)](../../../ado/guide/remote-data-service/rds-tutorial-vbscript.md)   
