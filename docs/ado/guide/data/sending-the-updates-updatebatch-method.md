---
title: 'Отправка обновлений: метод UpdateBatch | Документация Майкрософт'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 87123797-831f-48e0-94b5-f669f9ca194a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 182e444587ce9bb3ca73166fb05dfac2506a39aa
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67924256"
---
# <a name="sending-the-updates-updatebatch-method"></a>Отправка обновлений: метод UpdateBatch
Следующий код открывает набор записей в пакетном режиме, устанавливая для свойства LockType значение Адлоккбатчоптимистик, а CursorLocation — Адусеклиент. Он добавляет две новые записи и изменяет значение поля в существующей записи, сохраняет исходные значения, а затем вызывает UpdateBatch, чтобы отправить изменения обратно в источник данных.  
  
## <a name="remarks"></a>Remarks  
  
```  
'BeginBatchUpdate  
    strConn = "Provider=SQLOLEDB;Initial Catalog=Northwind;" & _  
              "Data Source=MySQLServer;Integrated Security=SSPI;"  
  
    strSQL = "SELECT ShipperId, CompanyName, Phone FROM Shippers"  
  
    Set objRs1 = New ADODB.Recordset  
    objRs1.CursorLocation = adUseClient  
    objRs1.Open strSQL, strConn, adOpenStatic, adLockBatchOptimistic, adCmdText  
  
    ' Change value of Phone field for first record in Recordset, saving value  
    ' for later restoration.  
    intId = objRs1("ShipperId")  
    sPhone = objRs1("Phone")  
  
    objRs1("Phone") = "(111) 555-1111"  
  
    'Add two new records  
    For i = 0 To 1  
        objRs1.AddNew  
        objRs1(1) = "New Shipper #" & CStr((i + 1))  
        objRs1(2) = "(nnn) 555-" & i & i & i & i  
    Next i  
  
    ' Send the updates  
    objRs1.UpdateBatch  
'EndBatchUpdate  
```  
  
 Если вы изменяете текущую запись или добавляете новую запись при вызове метода UpdateBatch, ADO автоматически вызывает метод Update, чтобы сохранить все ожидающие изменения в текущей записи перед передачей пакетных изменений поставщику.  
  
## <a name="see-also"></a>См. также:  
 [Пакетный режим](../../../ado/guide/data/batch-mode.md)
