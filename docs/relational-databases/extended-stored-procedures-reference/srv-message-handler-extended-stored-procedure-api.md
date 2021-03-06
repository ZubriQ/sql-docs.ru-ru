---
title: srv_message_handler (API-интерфейс расширенных хранимых процедур)
ms.custom: seo-dt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
apiname:
- srv_message_handler
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_message_handler
ms.assetid: 41bcd057-436f-4fa8-8293-fc8057a30877
author: rothja
ms.author: jroth
ms.openlocfilehash: 5a5aba02a9aaead76e7c9c3340de4f568160b307
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "74119394"
---
# <a name="srv_message_handler-extended-stored-procedure-api"></a>srv_message_handler (API-интерфейс расширенных хранимых процедур)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Используйте вместо этого интеграцию со средой CLR.  
  
 Вызывает установленный обработчик сообщений API-интерфейса расширенных хранимых процедур. Эта функция обычно используется для вызова [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] из расширенной хранимой процедуры, чтобы зарегистрировать ошибку (определенную расширенной хранимой процедурой) [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в файле журнала ошибок или [!INCLUDE[msCoName](../../includes/msconame-md.md)] журнале приложений Windows.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
int srv_message_handler (  
SRV_PROC *  
srvproc  
,  
int  
errornum  
,  
BYTE   
severity  
,  
BYTE  
state  
,  
int  
oserrnum  
,  
char *  
errtext  
,  
int  
errtextlen  
,  
char *  
oserrtext  
,  
int  
oserrtextlen  
);  
```  
  
## <a name="arguments"></a>Аргументы  
 *srvproc*  
 Указатель на структуру SRV_PROC, который представляет собой дескриптор соединения с клиентом. Параметр *srvproc* содержит сведения, которые используются для управления связью и передачей данных между приложением и клиентом.  
  
 *errornum*  
 Номер ошибки, определенный расширенной хранимой процедурой. Это значение должно быть от 50 001 до 2 147 483 647.  
  
 *severity*  
 Стандартное значение серьезности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для ошибки. Это значение должно быть от 0 до 24.  
  
 *state*  
 Значение состояния [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для ошибки.  
  
 *oserrnum*  
 Номер ошибки операционной системы. Этот аргумент не учитывается.  
  
 *errtext*  
 Описание ошибки *errornum* расширенной хранимой процедуры.  
  
 *errtextlen*  
 Длина строки ошибки *errtext* расширенной хранимой процедуры.  
  
 *oserrtext*  
 Описание ошибки операционной системы *oserrnum*. Этот аргумент не учитывается.  
  
 *oserrtextlen*  
 Длина строки ошибки операционной системы *oserrtext*.  
  
## <a name="returns"></a>Результаты  
 SUCCEED или FAIL.  
  
## <a name="remarks"></a>Remarks  
 Функция **srv_message_handler** обеспечивает интеграцию расширенной хранимой процедуры с централизованными функциями регистрации ошибок и подготовки отчетов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Можно назначить предупреждения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для событий из расширенных хранимых процедур, и агент SQL Server будет отслеживать состояние этих предупреждений.  
  
 Если сообщение об ошибке длиннее, оно усекается до 412 байт.  
  
> [!IMPORTANT]  
>  Необходимо тщательно просмотреть исходный код расширенных хранимых процедур и проверить скомпилированные библиотеки DLL перед их установкой на рабочий сервер. Сведения о проверке безопасности см. на следующем [веб-сайте Майкрософт](https://msdn.microsoft.com/security/).  
  
  
