---
title: MSSQL_ENG020557 | Документация Майкрософт
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG020557 error
ms.assetid: c43c6952-5b60-4347-b881-11a0004dce24
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: 6bb176bf9a18232f23cddd8446897383ae102f71
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "76288479"
---
# <a name="mssql_eng020557"></a>MSSQL_ENG020557
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
    
## <a name="message-details"></a>Сведения о сообщении  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|20557|  
|Источник события|MSSQLSERVER|  
|Компонент|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Символическое имя||  
|Текст сообщения|Завершение работы агента. Дополнительные сведения см. в журнале заданий агента SQL Server для задания «%s».|  
  
## <a name="explanation"></a>Объяснение  
 Агент репликации завершил работу, не записав причину в соответствующую таблицу журнала, либо работа агента была завершена в середине процесса.  
  
## <a name="user-action"></a>Действие пользователя  
  
-   Перезапустите агент и посмотрите, будет ли он теперь работать без сбоев. Дополнительные сведения см. в статьях и [Запуск и остановка агента репликации (среда SQL Server Management Studio)](../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md) и [Основные понятия исполняемых файлов агента репликации](../../relational-databases/replication/concepts/replication-agent-executables-concepts.md).  
  
-   Проверьте журнал агента и журнал заданий на наличие других ошибок, возникших приблизительно в то же время. Сведения о просмотре состояния агента и сведений об ошибках в мониторе репликации см. в статье [Просмотр сведений и выполнение задач с помощью монитора репликации](../../relational-databases/replication/monitor/view-information-and-perform-tasks-replication-monitor.md).  
 
-   Проверьте функционирование базовых соединений между компьютерами, к которым обращается агент, а затем подключитесь к каждому из этих компьютеров, используя программу, такую как **sqlcmd** . Для соединения используйте ту же учетную запись, под которой агент устанавливает соединения. Дополнительные сведения о правах доступа, необходимых учетной записи каждого агента, см. в разделе [Replication Agent Security Model](../../relational-databases/replication/security/replication-agent-security-model.md).  
  
-   Если ошибка возникает при создании или применении моментального снимка, проверьте файлы в каталоге моментальных снимков на наличие ошибок.  
  
-   Если ошибка продолжает возникать, увеличьте протоколирование агента и укажите выходной файл для журнала. В зависимости от контекста ошибки эта мера может помочь в определении шагов, которые приведут к ошибке или дополнительным сообщениям об ошибке. Дополнительные сведения о настройке ведения журнала репликации см. в статье базы знаний Майкрософт [312292](https://support.microsoft.com/kb/312292).  
  
## <a name="see-also"></a>См. также:  
 [Справочник по ошибкам и событиям (репликация)](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  
