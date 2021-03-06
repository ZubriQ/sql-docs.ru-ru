---
title: Руководство. Просмотр отчета советника по переходу | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- displaying reports
- viewing reports
- Upgrade Advisor [SQL Server], reports
- SQL Server Upgrade Advisor, reports
- reports [Upgrade Advisor], viewing
ms.assetid: d13b38af-0ac3-4030-83cd-e7d7825dd09f
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c0ae231e380530f11d4c97a917927ed62e99fb47
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66094794"
---
# <a name="how-to-view-an-upgrade-advisor-report"></a>Просмотр отчета помощника по обновлению
  Помощник по обновлению создает отчеты по каждому компоненту, выбранному для анализа. В этом разделе рассказывается о том, как просмотреть отчет помощника по обновлению с начальной страницы помощника по обновлению.  
  
> [!IMPORTANT]  
>  Средство просмотра отчетов загружает файлы, предполагая, что они имеют стандартные имена. Если файлы переименованы, средство просмотра отчетов их не загрузит.  
  
### <a name="to-view-a-report"></a>Просмотр отчета  
  
1.  Нажмите кнопку **Пуск**, выберите пункт **все программы**, затем **[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]**, а затем выберите ** [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] советник по переходу**.  
  
2.  На начальной странице советника по переходу щелкните **запустить средство просмотра отчетов помощника по обновлению**.  
  
3.  Чтобы выбрать отчет в каталоге по умолчанию на данном компьютере, выполните следующие действия.  
  
    1.  В списке **сервер** выберите сервер.  
  
    2.  В списке **экземпляр или компонент** выберите сочетание компонента или компонента или экземпляра.  
  
     Чтобы выбрать отчет в другом каталоге, выполните следующие действия.  
  
    1.  Щелкните ссылку **открыть отчет** .  
  
    2.  Перейдите в каталог, содержащий отчет, и дважды щелкните XML-файл.  
  
     Помощник по обновлению сохраняет до пяти отчетов, сформированных по итогам предыдущих анализов. Чтобы просмотреть эти отчеты, щелкните раскрывающийся список **отчет** и выберите отчет. Отчеты перечислены по меткам времени их создания.  
  
     Отчет содержит следующие дополнительные сведения по всем обнаруженным проблемам.  
  
    -   **Важность**, которая указывает, насколько важно устранить проблему.  
  
    -   **Когда следует исправить**, это указывает, следует ли (или необходимо) исправить проблему до или после обновления [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]до до или после миграции приложения или данных или в любое время.  
  
    -   Краткое описание проблемы.  
  
4.  Если отчет содержит более 20 элементов, щелкните зеленую стрелку «вперед» в верхней или нижней части отчета, чтобы просмотреть следующий набор элементов. Щелкните зеленую стрелку «назад», чтобы просмотреть предыдущие 20 элементов.  
  
5.  Чтобы отсортировать отчет, щелкните заголовок столбца.  
  
6.  Чтобы просмотреть дополнительные сведения по конкретному элементу, щелкните этот элемент. При этом появится описание проблемы и дополнительные параметры.  
  
    -   Чтобы просмотреть объекты, в которых обнаружена эта проблема, нажмите кнопку **Показать затронутые объекты**.  
  
    -   Чтобы просмотреть справку по этой неполадке, щелкните **Дополнительные сведения об этой неполадке и способах ее устранения**.  
  
    -   Чтобы отметить проблему как разрешенную, которая скрывает проблему при повторном просмотре отчета, выберите **эту проблему устранена**.  
  
> [!NOTE]  
>  Отчет может содержать элементы, указывающие на необнаруживаемые проблемы. Это проблемы, которые не могут быть обнаружены или формируют слишком много ложных положительных результатов. Щелкните **Дополнительные сведения об этой неполадке и разрешите ее** , чтобы просмотреть список необнаруживаемых проблем компонента.  
  
## <a name="see-also"></a>См. также  
 [Руководство. экспорт отчетов](../../../2014/sql-server/install/how-to-export-reports.md)   
 [Как запустить мастер анализа помощника по обновлению](../../../2014/sql-server/install/how-to-run-the-upgrade-advisor-analysis-wizard.md)   
 [Устранение проблем с обновлением](../../../2014/sql-server/install/resolving-upgrade-issues.md)   
 [Инструкции по советнику по переходу](../../../2014/sql-server/install/upgrade-advisor-how-to-topics.md)   
 [Работа с помощником по обновлению](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
