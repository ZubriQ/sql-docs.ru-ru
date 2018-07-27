---
title: Параметры запроса для профиля функциональной зависимости (задача "Профилирование данных") | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Data Profiling Task Editor
ms.assetid: 6eb853aa-8016-490c-be4f-06ab8d7f5021
caps.latest.revision: 23
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: b0988cccd7bed4112c901c3d5b5954fb7e4a991b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37318844"
---
# <a name="functional-dependency-profile-request-options-data-profiling-task"></a>Параметры запроса для профиля функциональной зависимости (задача «Профилирование данных»)
  Для установки параметров варианта **Запрос профиля функциональной зависимости** , выделенного на панели запросов, используется панель **Свойства запроса** страницы **Запросы профиля** . Профиль функциональной зависимости показывает, в какой степени значения в одном столбце (зависимом) зависят от значений в другом столбце или наборе столбцов (определяющем). Этот профиль также поможет выявить проблемы в данных, например наличие недопустимых значений. Например, выполняется профилирование зависимости между столбцом почтовых индексов США и столбцом штатов США. В этом профиле один и тот же почтовый индекс всегда должен соответствовать одному и тому же штату, но профиль обнаруживает нарушения этой зависимости.  
  
> [!NOTE]  
>  В этом разделе описываются параметры, расположенные на странице **Запросы профиля** в **редакторе задачи «Профилирование данных»**. Дополнительные сведения об этой странице редактора см. в разделе [Редактор задачи "Профилирование данных" (страница "Запросы профиля")](data-profiling-task-editor-profile-requests-page.md).  
  
 Дополнительные сведения об использовании задачи "Профилирование данных" см. в разделе [Установка задачи "Профилирование данных"](data-profiling-task.md). Дополнительные сведения об использовании средства просмотра профиля данных для анализа результатов задачи "Профилирование данных" см. в разделе [Средство просмотра профиля данных](data-profile-viewer.md).  
  
## <a name="understanding-the-selection-of-determinant-and-dependent-columns"></a>Основные сведения о выборе определяющих и зависимых столбцов  
 **Запрос профиля функциональной зависимости** вычисляет степень, в которой столбец или набор столбцов определяющей стороны (указанный в свойстве **DeterminantColumns** ) определяет значение столбца зависимой стороны (указанного в свойстве **DependentColumn** ). К примеру, столбец штатов США должен быть функционально зависимым от столбца почтовых индексов США. То есть, если значение почтового индекса (определяющий столбец) составляет 98052, значением штата (зависимого столбца) всегда будет Вашингтон.  
  
 Для определяющей стороны всегда можно указать столбец или набор столбцов в свойстве **DeterminantColumns** . Рассмотрим, к примеру, образец таблицы, содержащей столбцы A, B и С. Пользователь выбирает следующие элементы в свойстве **DeterminantColumns** .  
  
-   При выборе шаблона **(\*)** задача "Профилирование данных" проверяет каждый столбец как определяющую сторону зависимости.  
  
-   При выборе шаблона **(\*)**, а также другого столбца или столбцов задача "Профилирование данных" проверяет каждое сочетание столбцов как определяющую сторону зависимости. Рассмотрим, к примеру, образец таблицы, содержащей столбцы A, B и С. Если пользователь выбирает шаблон **(\*)** и столбец C в качестве значения свойства **DeterminantColumns**, задача "Профилирование данных" проверяет сочетания (A, C) и (B, C) в качестве определяющей стороны зависимости.  
  
 Для зависимой стороны можно указать один столбец или шаблон **(\*)** в свойстве **DependentColumn**. При выборе шаблона **(\*)** задача "Профилирование данных" проверяет столбец определяющей стороны или набор столбцов для каждого столбца.  
  
> [!NOTE]  
>  Возможно, что в случае выбора шаблона **(\*)** применение этого параметра вызовет необходимость выполнения большого объема вычислений, что приведет к снижению производительности при выполнении задачи. Однако если задача выявит подмножество, удовлетворяющее пороговому значению функциональной зависимости, эта задача не будет анализировать дополнительные сочетания. Например, если в описанном выше образце таблицы задача определяет, что столбец C является определяющим, задача не производит анализ составных кандидатов.  
  
## <a name="request-properties-options"></a>Параметры области «Свойства запроса»  
 Для варианта **Запрос профиля функциональной зависимости**на панели **Свойства запроса** отображаются следующие группы параметров.  
  
-   **Данные**, куда входят параметры **DeterminantColumns** и **DependentColumn**  
  
-   **Общие сведения**  
  
-   **Параметры**  
  
### <a name="data-options"></a>Параметры данных  
 **ConnectionManager**  
 Выберите существующий диспетчер подключений [!INCLUDE[vstecado](../../includes/vstecado-md.md)] , использующий поставщик данных .NET для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient) для подключения к базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , которая содержит таблицу или представление для профилирования.  
  
 **TableOrView**  
 Выберите существующую таблицу или представление для профилирования.  
  
 **DeterminantColumns**  
 Выберите определяющий столбец или набор столбцов. Иными словами, выберите столбец или набор столбцов, значения которых определяют значение зависимого столбца.  
  
 Дополнительные сведения см. в подразделах «Основные сведения о выборе определяющих и зависимых столбцов» и «Параметры DeterminantColumns и DependentColumn» в этом разделе.  
  
 **DependentColumn**  
 Выберите зависимый столбец. Иными словами, выберите столбец, значение которого определяется значением определяющего столбца или набора столбцов.  
  
 Дополнительные сведения см. в подразделах «Основные сведения о выборе определяющих и зависимых столбцов» и «Параметры DeterminantColumns и DependentColumn» в этом разделе.  
  
#### <a name="determinantcolumns-and-dependentcolumn-options"></a>Параметры DeterminantColumns и DependentColumn  
 Следующие параметры представлены для каждого столбца, выбранного для профилирования в параметрах **DeterminantColumns** и **DependentColumn**.  
  
 Дополнительные сведения см. в подразделе «Основные сведения о выборе определяющих и зависимых столбцов» выше в этом разделе.  
  
 **IsWildCard**  
 Указывает, выбран ли подстановочный знак **(\*)**. Этот параметр принимает значение **True**, если выбран подстановочный знак **(\*)**, означающий профилирование всех столбцов. Значение **False** показывает, что для профилирования выбран отдельный столбец. Этот параметр доступен только для чтения.  
  
 **ColumnName**  
 Отображает имя выбранного столбца. Этот параметр пуст, если выбран подстановочный знак **(\*)**, означающий профилирование всех столбцов. Этот параметр доступен только для чтения.  
  
 **StringCompareOptions**  
 Выберите параметры для сравнения строковых значений. Это свойство имеет параметры, указанные в следующей таблице. По умолчанию значение этого параметра равно **Default**.  
  
> [!NOTE]  
>  Если для свойства **ColumnName** используется шаблон **(\*)**, свойство **CompareOptions** доступно только для чтения и получает значение **Default**.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**Default**|Сортирует и сравнивает данные на основе параметров сортировки столбца в исходной таблице.|  
|**BinarySort**|Сортирует и сравнивает данные на основе битовых шаблонов, определенных для каждого символа. Двоичный порядок сортировки учитывает регистр и диакритические знаки. Двоичный порядок сортировки является самым быстрым.|  
|**DictionarySort**|Сортирует и сравнивает данные в соответствии с правилами сортировки и сравнения, определенными в словарях для соответствующего языка или алфавита.|  
  
 Если выбран вариант **DictionarySort**, можно дополнительно указать любое сочетание параметров, перечисленных в следующей таблице. По умолчанию эти дополнительные параметры не выбираются.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**IgnoreCase**|Указывает, следует ли при сравнении различать символы в верхнем и нижнем регистре. Если параметр задан, то строковое сравнение игнорирует регистр. Например, «ABC» при сравнении не отличается от «abc».|  
|**IgnoreNonSpace**|Указывает, следует ли при сравнении различать обычные символы и символы с диакритическими знаками. Если параметр задан, то строковое сравнение не учитывает диакритические знаки. Например, буква «a» с любыми диакритическими знаками будет считаться обычной буквой «a».|  
|**IgnoreKanaType**|Указывает, следует ли различать при сравнении два типа символов японской азбуки: хирагана и катакана. Если параметр задан, то строковое сравнение игнорирует тип японской азбуки.|  
|**IgnoreWidth**|Указывает, следует ли при сравнении различать однобайтовые символы или аналогичные двухбайтовые символы. Если параметр задан, то строковое сравнение рассматривает однобайтовое и двухбайтовое представления символа как один и тот же символ.|  
  
### <a name="general-options"></a>Общие параметры  
 **RequestID**  
 Введите описательное имя для этого запроса профиля. Обычно не нужно менять автоматически сформированное значение.  
  
### <a name="options"></a>Параметры  
 **ThresholdSetting**  
 Укажите пороговое значение. Значение этого свойства по умолчанию равно **Specified**.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**None**|Не задает пороговое значение. Степень функциональной зависимости указывается независимо от значения.|  
|**Specified**|Используется пороговое значение, указанное параметром **FDStrengthThreshold**. Степень функциональной зависимости указывается лишь в том случае, если она превышает пороговое значение.|  
|**Exact**|Не задает пороговое значение. Степень функциональной зависимости указывается лишь в том случае, если функциональная зависимость между выделенными столбцами является точной.|  
  
 **FDStrengthThreshold**  
 Укажите пороговое значение (между 0 и 1), при превышении которого необходимо сообщать о степени функциональной зависимости. Значение по умолчанию этого свойства равно 0,95. Этот параметр будет включен только в случае выбора для свойства **ThresholdSetting** значения **Определено**.  
  
 **MaxNumberOfViolations**  
 Укажите максимальное число нарушений функциональных зависимостей для сообщения в выводе. Значение по умолчанию этого свойства равно 100. Этот параметр будет выключен только в случае выбора для свойства **ThresholdSetting** значения **Точно**.  
  
## <a name="see-also"></a>См. также  
 [Редактор задачи "профилирование данных" &#40;страница "Общие"&#41;](../general-page-of-integration-services-designers-options.md)   
 [Форма быстрого профиля одной таблицы (задача "Профилирование данных")](single-table-quick-profile-form-data-profiling-task.md)  
  
  