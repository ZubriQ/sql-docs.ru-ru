---
title: Перенос данных DB2 в SQL Server (DB2ToSQL) | Документация Майкрософт
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 86cbd39f-6dac-409a-9ce1-7dd54403f84b
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 9cc7b3dd309dfac9e35021ca3234ca66483181e9
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68074106"
---
# <a name="migrating-db2-data-into-sql-server-db2tosql"></a>Перенос данных DB2 в SQL Server (DB2ToSQL)
После успешной синхронизации преобразованных объектов с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]можно перенести данные из DB2 в. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
> [!IMPORTANT]  
> Если используемый механизм является модулем миграции данных на стороне сервера, то перед переносом необходимо установить пакет расширения SSMA для DB2 и поставщики DB2 на компьютере, на котором выполняется SSMA. Также должна быть запущена служба агент SQL Server. Дополнительные сведения об установке пакета расширений см. в разделе Install [SSMA Components on SQL Server](https://msdn.microsoft.com/cf2b724b-4ca7-470a-8dd7-fa95b1e060a4)  
  
## <a name="setting-migration-options"></a>Настройка параметров миграции  
Перед переносом данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]в проверьте параметры миграции проекта в диалоговом окне " **Параметры проекта** ".  
  
-   С помощью этого диалогового окна можно задать такие параметры, как размер пакета миграции, блокировка таблицы, проверка ограничений, обработка значений NULL и обработка значений идентификаторов. Дополнительные сведения о параметрах миграции проекта см. в разделе [Параметры проекта (миграция)](https://msdn.microsoft.com/48aaa8e6-a9cb-487d-9ba5-fc3f1c4786ae).  
  
-   **Модуль миграции** в диалоговом окне **Параметры проекта** позволяет пользователю выполнить процесс миграции с помощью двух типов модулей миграции данных:  
  
    1.  Модуль миграции данных на стороне клиента  
  
    2.  Модуль миграции данных на стороне сервера  
  
**Перенос данных на стороне клиента:**  
  
-   Чтобы запустить миграцию данных на стороне клиента, выберите параметр **модуль миграции данных на стороне клиента** в диалоговом окне **Параметры проекта** .  
  
-   В **параметрах проекта**установлен параметр **модуль миграции данных на стороне клиента** .  
  
    > [!NOTE]  
    > **Модуль миграции данных на стороне клиента** находится внутри приложения SSMA и, следовательно, не зависит от доступности пакета расширений.  
  
**Перенос данных на стороне сервера:**  
  
-   Во время переноса данных на стороне сервера ядро размещается в целевой базе данных. Он устанавливается с помощью пакета расширений. Дополнительные сведения об установке пакета расширений см. в разделе Install [SSMA Components on SQL Server](https://msdn.microsoft.com/cf2b724b-4ca7-470a-8dd7-fa95b1e060a4)  
  
-   Чтобы начать миграцию на стороне сервера, выберите параметр **модуль миграции данных на стороне сервера** в диалоговом окне **Параметры проекта** .  
  
## <a name="migrating-data-to-sql-server"></a>Перенос данных в SQL Server  
Миграция данных — это операция групповой загрузки, которая перемещает строки данных из таблиц DB2 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в таблицы в транзакциях. Число строк, загружаемых [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в каждую транзакцию, настраивается в параметрах проекта.  
  
Чтобы просмотреть сообщения миграции, убедитесь, что панель вывода видна. В противном случае в меню **вид** выберите **выходные данные**.  
  
**Перенос данных**  
  
1.  Проверьте выполнение следующих условий.  
  
    -   Поставщики DB2 устанавливаются на компьютере, на котором выполняется SSMA.  
  
    -   Преобразованные объекты были синхронизированы с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базой данных.  
  
2.  В обозревателе метаданных DB2 выберите объекты, содержащие данные, которые необходимо перенести.  
  
    -   Чтобы перенести данные для всех схем, установите флажок рядом с пунктом **схемы**.  
  
    -   Чтобы перенести данные или пропустить отдельные таблицы, сначала разверните схему, разверните узел **таблицы**, а затем установите или снимите флажок рядом с таблицей.  
  
3.  Для миграции данных возникают два варианта:  
  
    **Перенос данных на стороне клиента:**  
  
    -   Для выполнения **переноса данных на стороне клиента**выберите параметр **модуль миграции данных на стороне клиента** в диалоговом окне " **Параметры проекта** ".  
  
    **Перенос данных на стороне сервера:**  
  
    -   Прежде чем выполнять миграцию данных на стороне сервера, убедитесь, что:  
  
        1.  Пакет расширения SSMA для DB2 устанавливается на экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
        2.  Служба агент SQL Server запущена на экземпляре SQL Server.  
  
    -   Для выполнения **переноса данных на стороне сервера**выберите параметр **модуль миграции данных на стороне сервера** в диалоговом окне " **Параметры проекта** ".  
  
4.  Щелкните правой кнопкой мыши **схемы** в ОБОЗРЕВАТЕЛЕ метаданных DB2 и выберите пункт **перенести данные**. Также можно выполнить миграцию данных для отдельных объектов или категорий объектов: щелкните правой кнопкой мыши объект или его родительскую папку. Выберите параметр **перенести данные** .  
  
    > [!NOTE]  
    > Если пакет расширений SSMA для DB2 не установлен на экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]и выбран **модуль миграции данных на стороне сервера** , то при переносе данных в целевую базу данных возникает следующая ошибка: ' SSMA Data Migration Components не найдено в SQL Server, миграция данных на стороне сервера не будет возможна. Убедитесь, что пакет расширений установлен правильно. Нажмите кнопку **Отмена** , чтобы завершить перенос данных.  
  
5.  В диалоговом окне **Подключение к DB2** введите учетные данные подключения и нажмите кнопку **подключить**. Дополнительные сведения о подключении к DB2 см. в статье [Подключение к базе данных db2 &#40;DB2ToSQL&#41;](../../ssma/db2/connecting-to-db2-database-db2tosql.md)  
  
    Для подключения к целевой базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]введите учетные данные подключения в диалоговом окне **Подключение к SQL Server** и нажмите кнопку **подключить**. Дополнительные сведения о подключении к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]см. в разделе [Подключение к SQL Server](https://msdn.microsoft.com/b59803cb-3cc6-41cc-8553-faf90851410e)  
  
    Сообщения будут отображаться в области **вывода** . По завершении миграции появится **отчет о переносе данных** . Если какие бы то ни было данные не были перенесены, щелкните строку, содержащую ошибки, а затем нажмите кнопку **сведения**. Завершив работу с отчетом, нажмите кнопку **Закрыть**. Дополнительные сведения об отчете о переносе данных см. в разделе [отчет о переносе данных (SSMA Common)](https://msdn.microsoft.com/bbfb9d88-5a98-4980-8d19-c5d78bd0d241) .  
  
> [!NOTE]  
> Если в качестве целевой базы данных используется SQL Express Edition, то разрешена только миграция данных на стороне клиента, а миграция данных на стороне сервера не поддерживается.  
  
## <a name="see-also"></a>См. также:  
[Перенос данных DB2 в SQL Server &#40;DB2ToSQL&#41;](../../ssma/db2/migrating-db2-data-into-sql-server-db2tosql.md)  
  
