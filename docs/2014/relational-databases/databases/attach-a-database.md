---
title: Присоединение базы данных | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.attachdatabase.f1
helpviewer_keywords:
- database attaching [SQL Server]
- attaching databases [SQL Server]
ms.assetid: b4efb0ae-cfe6-4d81-a4b4-6e4916885caa
caps.latest.revision: 44
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1cbf5e35d6bab800cfc025be9a7ca2bc4bc1b0e5
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37239054"
---
# <a name="attach-a-database"></a>Присоединение базы данных
  В этом разделе описывается присоединение базы данных в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. Эту функцию можно использовать для копирования, перемещения или обновления базы данных SQL Server.  
  
 **В этом разделе**  
  
-   **Перед началом работы выполните следующие действия.**  
  
     [Предварительные требования](#Prerequisites)  
  
     [Рекомендации](#Recommendations)  
  
     [безопасность](#Security)  
  
-   **Присоединение базы данных с помощью:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Дальнейшие действия.**  [После обновления базы данных](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Prerequisites"></a> Предварительные требования  
  
-   Базу данных сначала необходимо отсоединить. Попытка присоединить базу данных, которая не была отсоединена, приведет к возникновению ошибки. Дополнительные сведения см. в разделе [Отсоединение базы данных](detach-a-database.md).  
  
-   При присоединении базы данных должны быть доступны все файлы данных (файлы MDF и LDF). Если у какого-либо файла данных путь отличается от того, каким он был при первом создании или последнем присоединении, необходимо указать текущий путь к файлу.  
  
-   Если при присоединении базы данных файлы MDF и LDF находятся в разных каталогах, а один из путей содержит \\\\?\GlobalRoot, операция завершается ошибкой.  
  
###  <a name="Recommendations"></a> Рекомендации  
 Рекомендуется переносить базы данных с помощью процедуры запланированного переноса ALTER DATABASE, а не путем отсоединения и присоединения. Дополнительные сведения см. в статье [Move User Databases](move-user-databases.md).  
  
###  <a name="Security"></a> безопасность  
 Разрешения на доступ к файлам устанавливаются во время выполнения определенных операций с базами данных, включая отсоединение и присоединение баз данных. Дополнительные сведения о разрешениях доступа к файлам, задаваемые во время отсоединения и присоединения базы данных, см. в разделе [Защита данных и файлов журналов](http://technet.microsoft.com/library/ms189128.aspx) электронной документации по [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] .  
  
 Не рекомендуется подключать или восстанавливать базы данных, полученные из неизвестных или ненадежных источников. В этих базах данных может содержаться вредоносный код, вызывающий выполнение непредусмотренных инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)] или появление ошибок из-за изменения схемы или физической структуры базы данных. Перед тем как использовать базу данных, полученную из неизвестного или ненадежного источника, выполните на тестовом сервере инструкцию [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) для этой базы данных, а также изучите исходный код в базе данных, например хранимые процедуры и другой пользовательский код. Дополнительные сведения о присоединении баз данных и сведения об изменениях, вносимых при присоединении баз данных в метаданные, см. в статье [Присоединение и отсоединение базы данных (SQL Server)](database-detach-and-attach-sql-server.md).  
  
####  <a name="Permissions"></a> Permissions  
 Необходимо разрешение CREATE DATABASE, CREATE ANY DATABASE или ALTER ANY DATABASE.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-attach-a-database"></a>Присоединение базы данных  
  
1.  В обозревателе объектов среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] подключитесь к экземпляру [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]и разверните его.  
  
2.  Щелкните правой кнопкой мыши узел **Базы данных** и выберите команду **Присоединить**.  
  
3.  Чтобы указать присоединяемую базу данных, в диалоговом окне **Присоединение баз данных** нажмите кнопку **Добавить**, в диалоговом окне **Расположение файлов базы данных** выберите диск, на котором находится база данных, и разверните дерево каталогов, чтобы найти и выбрать MDF-файл, например:  
  
     `C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA\AdventureWorks2012_Data.mdf`  
  
    > [!IMPORTANT]  
    >  При попытке выбора базы данных, которая уже присоединена, возникает ошибка.  
  
     **Базы данных для присоединения**  
     Отобразятся сведения о выбранных базах данных.  
  
     \<нет заголовка столбца>  
     Отображается значок, указывающий на состояние операции присоединения. Возможные значки описываются в приводимом ниже описании **Состояние** .  
  
     **Расположение файла MDF**  
     Отображается путь и имя выбранного MDF-файла.  
  
     **Database Name**  
     Отображается имя базы данных.  
  
     **Присоединить как**  
     Необязательный параметр, указывает другое имя, под которым присоединяется база данных.  
  
     **Владелец**  
     Содержит раскрывающийся список возможных владельцев базы данных, из которого при необходимости можно выбрать другого владельца.  
  
     **Состояние**  
     Отображается состояние базы данных в соответствии со следующей таблицей.  
  
    |Значок|Текст состояния|Описание|  
    |----------|-----------------|-----------------|  
    |(Нет значка)|(Нет текста)|Операция присоединения не была запущена или находится в режиме ожидания для этого объекта. Это состояние по умолчанию при открытии диалогового окна.|  
    |Зеленый, указывающий направо треугольник|Выполняется|Операция присоединения была запущена, но не завершена.|  
    |Зеленый флажок|Успешно|Объект успешно присоединен.|  
    |Красный кружок с белым крестом внутри|Ошибка|При выполнении операции присоединения возникла ошибка, и операция не была успешно завершена.|  
    |Кружок с двумя черными квадратами (слева и справа) и двумя белыми квадратами (сверху и снизу)|Остановлена|Операция присоединения не была успешно завершена, т.к. пользователь остановил операцию.|  
    |Кружок, содержащий изогнутую стрелку, указывающую в направлении против часовой стрелки|Выполнен откат|Операция присоединения была успешной, но был выполнен ее откат из-за ошибки, возникшей при вложении другого объекта.|  
  
     **Сообщение**  
     Отображается пустое сообщение или гиперссылка «Файл не найден».  
  
     **Добавить**  
     Найдите необходимые основные файлы базы данных. Если пользователь выбирает mdf-файл, необходимые сведения автоматически вводятся в соответствующие поля сетки **Базы данных для присоединения** .  
  
     **Удалить**  
     Удаляет выбранный файл из сетки **Базы данных для присоединения** .  
  
     **"** *<database_name>* **" сведения о базе данных**  
     Отображаются имена файлов, которые необходимо присоединить. Чтобы проверить или изменить путь к файлу, нажмите кнопку **Обзор** (**…**).  
  
    > [!NOTE]  
    >  Если файл не существует, в столбце **Сообщение** отображается сообщение «Не найден». Если файл журнала не найден, то он существует в другом каталоге или был удален. Необходимо или обновить путь файла в сетке **Сведения о базе данных** таким образом, чтобы этот путь указывал на правильное расположение, или удалить файл журнала из сетки. Если MDF-файл не найден, необходимо обновить путь этого файла в сетке таким образом, чтобы этот путь указывал на правильное расположение.  
  
     **Имя исходного файла**  
     Отображается имя присоединенного файла, принадлежащего базе данных.  
  
     **Тип файла**  
     Указывается тип файла: **Данные** или **Журнал**.  
  
     **Текущий путь к файлу**  
     Отображается путь к выбранному файлу базы данных. Путь может быть изменен вручную.  
  
     **Сообщение**  
     Отображается пустое сообщение или гиперссылка "**Файл не найден**".  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-attach-a-database"></a>Присоединение базы данных  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели "Стандартная" нажмите **Создать запрос**.  
  
3.  Выполните инструкцию [CREATE DATABASE](/sql/t-sql/statements/create-database-sql-server-transact-sql) с предложением FOR ATTACH.  
  
     Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере производится присоединение файлов базы данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] с ее последующим переименованием в `MyAdventureWorks`.  
  
    ```  
    CREATE DATABASE MyAdventureWorks   
        ON (FILENAME = 'C:\MySQLServer\AdventureWorks_Data.mdf'),   
        (FILENAME = 'C:\MySQLServer\AdventureWorks_Log.ldf')   
        FOR ATTACH;  
  
    ```  
  
    > [!NOTE]  
    >  Кроме того, можно вызвать хранимую процедуру [sp_attach_db](/sql/relational-databases/system-stored-procedures/sp-attach-db-transact-sql) или [sp_attach_single_file_db](/sql/relational-databases/system-stored-procedures/sp-attach-single-file-db-transact-sql) . Но эти расширенные хранимые процедуры в будущих версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]будут удалены. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Рекомендуем использовать инструкцию CREATE DATABASE … FOR ATTACH.  
  
##  <a name="FollowUp"></a> Продолжение: после обновления базы данных SQL Server  
 После обновления базы данных при помощи описанного метода присоединения, эта база данных сразу становится доступной, после чего обновляется автоматически. Если база данных содержит полнотекстовые индексы, то в процессе обновления будет произведен их импорт, сброс или перестроение в зависимости от установленного значения свойства сервера **Режим обновления полнотекстового каталога** . Если при обновлении выбран режим **Импортировать** или **Перестроить**, то полнотекстовые индексы во время обновления будут недоступны. В зависимости от объема индексируемых данных процесс импорта может занять несколько часов, а перестроение — в несколько (до десяти) раз больше. Обратите внимание, что если при обновлении выбран режим **Импортировать**, а полнотекстовый каталог недоступен, то связанные с ним полнотекстовые индексы будут перестроены.  
  
 Если уровень совместимости пользовательской базы данных до обновления был 100 или выше, после обновления он останется таким же. Если уровень совместимости до обновления был 90, в обновленной базе данных он устанавливается в 100, что является минимально поддерживаемым уровнем совместимости в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Дополнительные сведения см. в разделе [Уровень совместимости инструкции ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level).  
  
## <a name="see-also"></a>См. также  
 [CREATE DATABASE (SQL Server Transact-SQL)](/sql/t-sql/statements/create-database-sql-server-transact-sql)   
 [Отсоединение базы данных](detach-a-database.md)  
  
  