---
title: Часто задаваемые вопросы об ODBC в Linux и macOS | Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 65bfd6d2-c83d-4528-a5e1-a85b125a4f4a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b266913d6e8e1a073c8831880ddcd4938b2b9dc9
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80921931"
---
# <a name="frequently-asked-questions-faq-for-odbc-linux-and-macos"></a>Часто задаваемые вопросы об ODBC в Linux и macOS
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Ниже приведены ответы на вопросы о драйвере ODBC для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в Linux и macOS.
  
## <a name="frequently-asked-questions"></a>Часто задаваемые вопросы

**Как работают с драйвером существующие приложения ODBC в Linux и macOS?**  
Вы должны быть в состоянии компилировать и запускать приложения ODBC, которые компилировались и запускались в Linux или macOS с использованием других драйверов. 
  
**Какие функции [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] поддерживает эта версия драйвера?**

Драйвер ODBC для Linux и macOS поддерживает все функции сервера в [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], за исключением LocalDB. Дополнительные сведения о поддерживаемых функциях [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] см. в статье [Programming Guidelines](../../../connect/odbc/linux-mac/programming-guidelines.md).  
  
**Поддерживает ли драйвер проверку подлинности Kerberos?**  
Да. При наличии существующей установки среды Kerberos вы сможете подключиться к серверам, используя имя DSN `Trusted_Connection=Yes` или строку подключения. Дополнительные сведения см. в статье [Использование встроенной проверки подлинности](../../../connect/odbc/linux-mac/using-integrated-authentication.md).  
  
**Какую кодировку Юникода должно использовать приложение?**  
UTF-8 для данных SQL_CHAR и UTF-16 для данных SQL_WCHAR. В зависимости от языкового стандарта и версии драйвера, могут поддерживаться данные и в некоторых других кодировках, кроме UTF-8. Более подробную информацию см. в статье [Указания по программированию](../../../connect/odbc/linux-mac/programming-guidelines.md).

**Существуют ли примеры ODBC, которые я могу скачать и запустить с помощью драйвера, чтобы поэкспериментировать с ним или оценить его?**

Пример см. в статье [Использование существующих примеров MSDN C++ ODBC для драйвера ODBC в Linux](https://blogs.msdn.com/b/sqlblog/archive/2012/01/26/use-existing-msdn-c-odbc-samples-for-microsoft-linux-odbc-driver.aspx) . Это также применимо к драйверу ODBC для macOS. 

**Имеет ли драйвер ODBC для Linux открытый исходный код?**

Нет, драйвер ODBC для Linux не является продуктом с открытым исходным кодом.  

## <a name="see-also"></a>См. также:

- [Установка Microsoft ODBC Driver for SQL Server в Linux](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)
- [Установка Microsoft ODBC Driver for SQL Server в macOS](../../../connect/odbc/linux-mac/install-microsoft-odbc-driver-sql-server-macos.md)
