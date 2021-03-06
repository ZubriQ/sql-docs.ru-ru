---
title: Скрытие элемента (построитель отчетов и службы SSRS) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.shared.visibility.f1
- "10503"
ms.assetid: 9d78f8de-959b-456f-8947-687fa6e2ba91
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d0eb06c9136179a075057791f88bf2d80e187026
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "78176885"
---
# <a name="hide-an-item-report-builder-and-ssrs"></a>Скрытие элемента (построитель отчетов и службы SSRS)
  Если необходимо скрывать элемент в зависимости от параметра отчета или другого указанного выражения, то можно настроить видимость для этого элемента отчета.

 Отчет можно разработать таким образом, чтобы позволить пользователям переключать видимость элементов отчета, щелкая текстовые поля, например, для вывода отчета с углубленной детализацией. Дополнительные сведения см. в разделе [Добавление действия "Развернуть" или "Свернуть" к элементу (построитель отчетов и службы SSRS)](../report-design/add-an-expand-or-collapse-action-to-an-item-report-builder-and-ssrs.md).

 В следующих процедурах показывается, как можно скрыть или отобразить элемент отчета, готового для просмотра, на основе значения константы или выражения.

> [!NOTE]
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]

### <a name="to-hide-a-report-item"></a>Скрытие элемента отчета

1.  В представлении конструктора отчетов щелкните правой кнопкой мыши элемент отчета и откройте страницу **Свойства** .

    > [!NOTE]
    >  Для выбора целой таблицы или матричной области данных щелкните в области данных, чтобы выбрать ее, затем щелкните правой кнопкой мыши маркер строки или столбца либо угловой маркер и выберите пункт **Свойства табликса**.

2.  Нажмите кнопку **видимость.**

3.  В поле **При первом запуске отчета**укажите, следует ли скрыть элемент при первом просмотре отчета.

    -   Чтобы отобразить элемент, щелкните **Показать**.

    -   Чтобы скрыть его, щелкните **Скрыть**.

    -   Чтобы указать выражение, которое будет вычисляться во время выполнения, щелкните **Отображать или скрывать в зависимости от выражения**. Введите выражение или нажмите кнопку (**fx**), чтобы создать выражение в диалоговом окне **Выражение** .

        > [!NOTE]
        >  Когда вы определяете выражения для видимости, вы настраиваете свойство Hidden элемента отчета, как показано на следующем изображении. Данное вычисляемое выражение отображает элемент отчета, если значение равно False и скрывает его, если значение равно True. 
        > ![Свойства_Диалоговое окно "Видимость" и свойство Hidden](../media/hiddenproperty-propertiesvisibility.png "Свойства_Диалоговое окно "Видимость" и свойство Hidden")

4.  Щелкните дважды **ОК**.

### <a name="to-hide-static-rows-in-a-table-matrix-or-list"></a>Скрытие статических строк в таблице, матрице или списке

1.  В представлении конструктора отчетов щелкните таблицу, матрицу или список, чтобы показать маркеры строк и столбцов.

2.  Щелкните правой кнопкой мыши маркер строки и выберите пункт **Видимость строки**. Откроется диалоговое окно **Видимость строки** .

3.  Чтобы настроить видимость, выполните шаги 3 и 4 первой процедуры.

### <a name="to-hide-static-columns-in-a-table-matrix-or-list"></a>Скрытие статических столбцов в таблице, матрице или списке

1.  В режиме конструктора выберите таблицу, матрицу или список, чтобы показать маркеры строк и столбцов.

2.  Щелкните правой кнопкой мыши маркер столбца и выберите пункт **Видимость столбца**.

3.  В диалоговом окне **Видимость столбца** повторите шаги 3 и 4 первой процедуры.

## <a name="see-also"></a>См. также:
 [Действие углубленной детализации &#40;построитель отчетов и SSRS&#41;](../report-design/drilldown-action-report-builder-and-ssrs.md) [Добавить действие "развернуть" или "Свернуть" в элемент &#40;ПОСТРОИТЕЛЬ отчетов и службы SSRS&#41;,](../report-design/add-an-expand-or-collapse-action-to-an-item-report-builder-and-ssrs.md) [примеры](../report-design/expression-examples-report-builder-and-ssrs.md) &#40;построитель отчетов и службы SSRS&#41;


