---
title: Функция Склремоветранслатор | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLRemoveTranslator
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLRemoveTranslator
helpviewer_keywords:
- SQLRemoveTranslator function [ODBC]
ms.assetid: c6feda49-0359-4224-8de9-77125cf2397b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 348d2c5da0731ba88ccd4dd6406d3754890f7906
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81301791"
---
# <a name="sqlremovetranslator-function"></a>Функция SQLRemoveTranslator
**Соответствия**  
 Введенная версия: ODBC 3,0  
  
 **Сводка**  
 **Склремоветранслатор** удаляет сведения о трансляторе из раздела Odbcinst. ini сведений о системе и уменьшает счетчик использования компонентов транслятора на 1.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
  
BOOL SQLRemoveTranslator(  
     LPCSTR    lpszTranslator,  
     LPDWORD   lpdwUsageCount);  
```  
  
## <a name="arguments"></a>Аргументы  
 *лпсзтранслатор*  
 Входной Имя транслятора, зарегистрированное в ключе Odbcinst. ini системных сведений.  
  
 *лпдвусажекаунт*  
 Проверки Число использований транслятора после вызова этой функции.  
  
## <a name="returns"></a>Результаты  
 Функция возвращает TRUE, если она успешна, и FALSE в случае сбоя. Если при вызове этой функции в системной информации не существует записи, функция возвращает значение FALSE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **склремоветранслатор** возвращает значение false, связанное * \*значение пферроркоде* может быть получено путем вызова **склинсталлереррор**. В следующей таблице перечислены значения * \*пферроркоде* , которые могут быть возвращены **склинсталлереррор** , и объясняется каждый из них в контексте этой функции.  
  
|*\*пферроркоде*|Error|Описание|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Общая ошибка установщика|Произошла ошибка, для которой не возникала конкретная ошибка установщика.|  
|ODBC_ERROR_COMPONENT_NOT_FOUND|Компонент не найден в реестре|Установщику не удалось удалить данные транслятора, так как они не существовали в реестре или не найдены в реестре.|  
|ODBC_ERROR_INVALID_NAME|Недопустимое имя драйвера или транслятора|Недопустимый аргумент *лпсзтранслатор* .|  
|ODBC_ERROR_USAGE_UPDATE_FAILED|Не удалось увеличить или уменьшить счетчик использования компонентов|Установщику не удалось уменьшить счетчик использования драйвера.|  
|ODBC_ERROR_OUT_OF_MEM|Недостаточно памяти|Установщику не удалось выполнить функцию из-за нехватки памяти.|  
  
## <a name="comments"></a>Комментарии  
 **Склремоветранслатор** дополняет функцию [склинсталлтранслаторекс](../../../odbc/reference/syntax/sqlinstalltranslatorex-function.md) и обновляет счетчик использования компонентов в системных сведениях. Эта функция должна вызываться только из приложения установки.  
  
 **Склремоветранслатор** уменьшит число использований компонента на 1. Если счетчик использования компонентов переходит в значение 0, запись транслятора в системных данных будет удалена. Запись переводчика находится в следующем расположении в разделе "сведения о системе" под именем переводчика:  
  
 `HKEY_LOCAL_MACHINE`  
  
 `SOFTWARE`  
  
 `ODBC`  
  
 `Odbcinst.ini`  
  
 **Склремоветранслатор** на самом деле не удаляет никакие файлы. Вызывающая программа отвечает за удаление файлов и поддержку счетчика использования файлов. Только после того, как счетчик использования компонента и счетчик использования файлов достигли нуля, физически удаляется файл. Некоторые файлы компонента могут быть удалены, а другие не удаляются в зависимости от того, используются ли файлы другими приложениями, увеличивающими число использованных файлов.  
  
 **Склремоветранслатор** также вызывается как часть процесса обновления. Если приложение обнаруживает, что оно должно выполнить обновление и ранее установило драйвер, драйвер следует удалить, а затем установить заново. Сначала необходимо вызвать **склремоветранслатор** , чтобы уменьшить число использованных компонентов, а затем вызвать **склинсталлтранслаторекс** , чтобы увеличить число использований компонента. Программа установки приложения должна физически заменить старые файлы новыми файлами. Количество использованных файлов останется прежним, а другие приложения, использующие более старые версии файлов, теперь будут использовать более новую версию.  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Установка транслятора|[склинсталлтранслаторекс](../../../odbc/reference/syntax/sqlinstalltranslatorex-function.md)|
