---
title: Элемент HelpLink | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- HelpLink element
- SoapException class
ms.assetid: a4489103-a874-44c2-8f75-95cb238928ed
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7bdd18641663003a1878fe0af0ac1d39a16eda1f
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "63046030"
---
# <a name="helplink-element"></a>Элемент HelpLink
  Элемент **HelpLink** свойства **Detail** представляет строку с URL-адресом, которая создается сервером отчетов. Этот URL-адрес ссылается на веб-страницу, управляемую центром справки и поддержки [!INCLUDE[msCoName](../../../includes/msconame-md.md)], которая предоставляет дополнительную справку и статьи базы значений, посвященные ошибкам, происходящим в службах [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. URL-адрес имеет следующий синтаксис:  
  
 **http://** www.Microsoft.com**/****/** Products**/** ee Transform. aspx **? Значение евтсрк**=_value_ **&евтид**=_значение_ **&ProdName**=_значение_ **&продвер**=_value_  
  
 В следующей таблице перечислены аргументы URL-адреса **HelpLink**.  
  
|Аргумент|Применение|  
|--------------|-----------|  
|**EvtSrc**|Microsoft.ReportingServices.Diagnostics.ErrorStrings.resources.Strings.|  
|**EvtID**|Код ошибки сервера отчетов, например rsReservedItem.|  
|**ProdName**|«Microsoft SQL%20Server%20Reporting%20Services». Значение названия продукта кодируется по правилам URL-адресов.|  
|**ProdVer**|Номер версии служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. Значение "8,00" означает [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].|  
  
 В следующем примере показан URL-адрес **HelpLink** , который возвращается для кода `rsReservedItem`ошибки. Эта ошибка происходит, когда пользователь выполняет попытку изменить или удалить зарезервированный элемент в службах [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]:  
  
```  
https://www.microsoft.com/products/ee/transform.aspx?  
EvtSrc=Microsoft.ReportingServices.Diagnostics.ErrorStrings.resources.Strings  
&EvtID=rsReservedItem&ProdName=Microsoft%20SQL%20Server%20Reporting%20Services&ProdVer=8.00  
```  
  
 Доступ к элементу **HelpLink** можно получить из программного кода с помощью класса **SoapException**.  
  
```vb  
Try  
   rs.DeleteItem("/Report1")  
  
Catch e As SoapException  
   Console.WriteLine(e.Detail("HelpLink").InnerXml)  
End Try  
```  
  
```csharp  
try  
{  
   rs.DeleteItem("/Report1");  
}  
  
catch (SoapException e)  
{  
   Console.WriteLine(e.Detail["HelpLink"].InnerXml);  
}  
```  
  
## <a name="see-also"></a>См. также  
 [Введение в обработку исключений в Reporting Services](../introducing-exception-handling-in-reporting-services.md)   
 [Reporting Services класс SoapException](reporting-services-soapexception-class.md)   
 [Использование свойства Detail для обработки определенных ошибок](../best-practices/using-the-detail-property-to-handle-specific-errors.md)  
  
  
