---
title: Параметры объекта команды | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Command object [ADO], parameters
ms.assetid: 10e7ef4a-78bf-4e91-931e-cbc6c065dd4c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 29ad7f3aa9347af77080b04fb309f8b50b95dbe4
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67925879"
---
# <a name="command-object-parameters"></a>Параметры объекта Command
В предыдущем разделе обсуждалось [Создание и исполнение простой команды](../../../ado/guide/data/creating-and-executing-a-simple-command.md). Более интересное использование объекта [Command](../../../ado/reference/ado-api/command-object-ado.md) показано в следующем примере, в котором команда SQL была параметризована. Это изменение позволяет повторно использовать команду, одновременно передавая ей другое значение параметра. Так как свойство [подготовленного свойства](../../../ado/reference/ado-api/prepared-property-ado.md) для объекта **Command** имеет значение **true**, ADO потребует от поставщика компилировать команду, указанную в параметре [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) , прежде чем выполнять ее в первый раз. Она также будет хранить скомпилированную команду в памяти. Это снижает скорость выполнения команды при первом ее выполнении из-за накладных расходов, необходимых для ее подготовки, но приводит к повышению производительности при каждом вызове команды. Поэтому команды должны быть подготовлены, только если они будут использоваться более одного раза.  
  
```  
'BeginManualParamCmd  
    On Error GoTo ErrHandler:  
  
    Dim objConn As New ADODB.Connection  
    Dim objCmd As New ADODB.Command  
    Dim objParm1 As New ADODB.Parameter  
    Dim objRs As New ADODB.Recordset  
  
    ' Set the CommandText as a parameterized SQL query.  
    objCmd.CommandText = "SELECT OrderID, OrderDate, " & _  
                         "RequiredDate, ShippedDate " & _  
                         "FROM Orders " & _  
                         "WHERE CustomerID = ? " & _  
                         "ORDER BY OrderID"  
    objCmd.CommandType = adCmdText  
  
    ' Prepare command because we will be executing it more than once.  
    objCmd.Prepared = True  
  
    ' Create new parameter for CustomerID. Initial value is ALFKI.  
    Set objParm1 = objCmd.CreateParameter("CustId", adChar, _  
                    adParamInput, 5, "ALFKI")  
    objCmd.Parameters.Append objParm1  
  
    ' Connect to the data source.  
    Set objConn = GetNewConnection  
    objCmd.ActiveConnection = objConn  
  
    ' Execute once and display.  
    Set objRs = objCmd.Execute  
  
    Debug.Print objParm1.Value  
    Do While Not objRs.EOF  
        Debug.Print vbTab & objRs(0) & vbTab & objRs(1) & vbTab & _  
                    objRs(2) & vbTab & objRs(3)  
        objRs.MoveNext  
    Loop  
  
    ' .Set new param value, re-execute command, and display.  
    objCmd("CustId") = "CACTU"  
    Set objRs = objCmd.Execute  
  
    Debug.Print objParm1.Value  
    Do While Not objRs.EOF  
        Debug.Print vbTab & objRs(0) & vbTab & objRs(1) & vbTab & _  
                    objRs(2) & vbTab & objRs(3)  
        objRs.MoveNext  
    Loop  
  
    'clean up  
    objRs.Close  
    objConn.Close  
    Set objRs = Nothing  
    Set objConn = Nothing  
    Set objCmd = Nothing  
    Set objParm1 = Nothing  
    Exit Sub  
  
ErrHandler:  
    'clean up  
    If objRs.State = adStateOpen Then  
        objRs.Close  
    End If  
  
    If objConn.State = adStateOpen Then  
        objConn.Close  
    End If  
  
    Set objRs = Nothing  
    Set objConn = Nothing  
    Set objCmd = Nothing  
    Set objParm1 = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
'EndManualParamCmd  
  
'BeginNewConnection  
Private Function GetNewConnection() As ADODB.Connection  
    Dim oCn As New ADODB.Connection  
    Dim sCnStr As String  
  
    sCnStr = "Provider='SQLOLEDB';Data Source='MySqlServer';" & _  
             "Integrated Security='SSPI';Initial Catalog='Northwind';"  
    oCn.Open sCnStr  
  
    If oCn.State = adStateOpen Then  
        Set GetNewConnection = oCn  
    End If  
  
End Function  
'EndNewConnection  
```  
  
 Не все поставщики поддерживают подготовленные команды. Если поставщик не поддерживает подготовку команд, он может вернуть сообщение об ошибке, как только это свойство будет установлено в **значение true**. Если она не возвращает ошибку, запрос на подготовку команды пропускается и присваивает свойству **Prepared** **значение false**.
