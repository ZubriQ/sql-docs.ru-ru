---
title: Метод Execute (RDS) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Execute method [ADO]
ms.assetid: 2d9c30e9-ab5b-4920-91b8-48454c2fb5d8
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d1a5fa5c9002d4a27490dfc98fb79f482539f042
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67964316"
---
# <a name="execute-method-rds"></a>Метод Execute (служба удаленных рабочих столов)
Выполняет запрос и создает набор записей ADO для использования в ADO 2,5 и более поздних версиях.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, компоненты RDS больше не включены в операционную систему Windows (Дополнительные сведения см. в статье о совместимости Windows 8 и [Windows server 2012 Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). Клиентские компоненты RDS будут удалены в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие RDS, должны переноситься в [службу данных WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object.Execute(ConnectionString As String, HandlerString As String, QueryString As String, lFetchOptions As Long, Properties, TableId, lExecuteOptions As Long, pParameters, [lcid As Long], [pInformation])  
```  
  
#### <a name="parameters"></a>Параметры  
 *ConnectionString*  
 Строка, используемая для подключения к поставщику OLE DB, в котором запрос будет отправлен для выполнения. Если обработчик указан с помощью *хандлерстринг* , он может изменить или заменить строку подключения.  
  
 *хандлерстринг*  
 Строка из двух частей, определяющая обработчик, который будет использоваться с этим выполнением. Строка содержит две части. Первая часть содержит имя (ProgID) используемого обработчика. Вторая часть содержит аргументы, передаваемые в обработчик. Сведения о том, как интерпретируется строка аргументов, относятся к каждому обработчику. Две части разделяются первым экземпляром запятой в строке. Строка arguments может содержать дополнительные запятые. Аргументы являются необязательными.  
  
 *QueryString*  
 Команда на языке команд, поддерживаемая поставщиком OLE DB, указанным в строке подключения. Для поставщиков на основе SQL *строка запроса* может содержать инструкцию TRANSACT-SQL, но для поставщиков, отличных от SQL (например, мсдаташапе), это может быть не [!INCLUDE[tsql](../../../includes/tsql-md.md)] Инструкция запроса.  
  
 Если используется обработчик, обработчик может изменить или заменить указанное здесь значение. Например, обработчик обычно заменяет *QueryString* строкой запроса из ini-файла. По умолчанию используется файл Мсдфмап. ini.  
  
 *лфетчоптионс*  
 Указывает тип асинхронной выборки.  
  
 Дополнительные сведения см. в разделе [свойство FetchOptions (RDS)](../../../ado/reference/rds-api/fetchoptions-property-rds.md).  
  
 *TableID*  
 **Вариант** типа либо VT_EMPTY, либо VT_BSTR. Если это значение имеет тип VT_EMPTY, оно игнорируется. Если он имеет тип VT_BSTR, набор записей создается с помощью **адкмдтабледирект** , а значение, указанное здесь, и параметр *QueryString* игнорируется.  
  
 *лексекутеоптионс*  
 Битовая маска параметров выполнения:  
  
 1 =*только для чтения* , набор записей будет открыт с помощью **адлоккреадонли**.  
  
 2 =*Непакетированный* набор записей будет открыт с помощью **adLockOptimistic**.  
  
 4 =*аллпараминфосупплиед* . вызывающий объект гарантирует, что сведения о параметрах для всех параметров передаются в *ппараметерс*.  
  
 8 =*сведения о* параметрах для запроса будут получены от поставщика OLE DB и возвращены в параметре *ппараметерс* . Запрос не выполняется, и набор записей не возвращается.  
  
 16 =*жесидденколумнс* набор записей будет открыт с помощью **адлоккбатчоптимистик** , а все скрытые столбцы будут включаться в набор записей.  
  
 *ReadOnly*, *unbatch* и *жесидденколумнс* являются взаимоисключающими параметрами; Однако он не создает ошибку для установки более чем одного из них. Если задано несколько параметров, *жесидденколумнс* имеет приоритет над всеми остальными, за которым следует *только ReadOnly*. Если параметры не указаны, по умолчанию набор записей открывается с помощью **адлоккбатчоптимистик** , а скрытые столбцы не включаются в набор записей.  
  
 *ппараметерс*  
 **Значение типа Variant** , содержащее надежный массив определений параметров. Если параметр " *info* " был указан в *лексекутеоптионс*, этот параметр используется для возврата определений параметров, полученных от поставщика OLE DB. В противном случае этот параметр может быть пустым.  
  
 *lcid*  
 КОД языка, используемый для создания любых ошибок, возвращаемых в *пинформатион*.  
  
 *пинформатион*  
 Указатель на информационную ошибку, возвращенную инструкцией EXECUTE. Если значение равно NULL, сведения об ошибке не возвращаются.  
  
## <a name="remarks"></a>Remarks  
 Параметр *хандлерстринг* может иметь значение null. Что происходит в этом случае, зависит от настройки сервера RDS. Строка обработчика "МСДФМАП. Handler" указывает, что следует использовать предоставляемый корпорацией Майкрософт обработчик (Мсдфмап. dll). Строка обработчика "МАСДФМАП. Handler; Sample. ini" указывает, что должен использоваться обработчик Мсдфмап. dll, а аргумент "Sample. ini" должен быть передан обработчику. МСДФМАП. dll интерпретирует аргумент как направление использования файла Sample. ini для проверки соединения и строк запроса.  
  
## <a name="applies-to"></a>Применяется к  
 [Объект DataFactory (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)


