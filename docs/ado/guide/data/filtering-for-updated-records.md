---
title: Фильтрация обновленных записей | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- filtering for updated records [ADO]
ms.assetid: 4a798921-d7bb-47c9-a252-550fd9463ec9
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0b5afe84664719da5a1dbc7777aef524be28c459
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67925338"
---
# <a name="filtering-for-updated-records"></a>Фильтрация обновленных записей
Перед вызовом UpdateBatch можно использовать свойство фильтра набора записей для просмотра только тех записей, которые были изменены с момента открытия набора записей, или последнего вызова UpdateBatch. Для этого установите фильтр равное Адфилтерпендингрекордс, чтобы определить, сколько записей будет Обновлено, как показано в примере кода в следующем разделе.  
  
## <a name="remarks"></a>Remarks  
 Этот пример расширяет предыдущий пример UpdateBatch, отфильтровывая набор записей непосредственно перед вызовом UpdateBatch, отображая пользователя, какие записи изменятся, и позволяя отменить обновление (с помощью метода CancelBatch).  
  
```  
'BeginFilterPend  
    '...  
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
  
    objRs1.Filter = adFilterPendingRecords  
  
    MsgBox "There are " & objRs1.RecordCount & " records pending.", _  
            , "Filter Pending"  
  
    ' Cancel the updates  
    objRs1.CancelBatch  
'EndFilterPend  
```  
  
## <a name="see-also"></a>См. также:  
 [Пакетный режим](../../../ado/guide/data/batch-mode.md)
