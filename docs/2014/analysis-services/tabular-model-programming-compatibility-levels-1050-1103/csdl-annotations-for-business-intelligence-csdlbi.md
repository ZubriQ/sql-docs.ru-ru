---
title: Аннотации языка CSDL для бизнес-аналитики (CSDLBI) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
ms.assetid: bf6f372a-bc67-45ea-a771-b2dc5b0527e5
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0348c262453d2de8e4db0c379b5bf70a2d7d7977
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "79525455"
---
# <a name="csdl-annotations-for-business-intelligence-csdlbi"></a>Заметки языка CSDL для бизнес-аналитики (CSDLBI)
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] поддерживает представление определения табличной модели в формате XML, называемое языком определения концептуальной схемы с заметками бизнес-аналитики (CSDLBI).  
  
 В этом разделе представлены общие сведения о CSDLBI и его использовании в моделях данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
## <a name="understanding-the-role-of-csdl"></a>Основные сведения о роли языка CSDL  
 Язык концептуальной схемы данных (CSDL) — это язык на основе XML, описывающий сущности, связи и функции. Язык CSDL определен как часть платформы Entity Data Framework. Заметки бизнес-аналитики — это расширение, разработанное для поддержки моделирования данных с помощью [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
 Несмотря на то что язык CSDL совместим с платформой Entity Data Framework, для построения с его помощью табличной модели или основанного на модели отчета не требуются ни знания модели «сущность-связь», ни какие-либо специальные средства. Модели создаются с помощью клиентских средств, таких как [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], или API, таких как объекты AMO, и развертываются на сервере. Клиенты подключаются к модели с помощью файла определения модели, обычно публикуемого в библиотеке SharePoint, где его могут использовать конструкторы отчетов и пользователи отчетов. Для просмотра дополнительных сведений перейдите по следующим ссылкам:  
  
-   [Решения табличных моделей (табличные службы SSAS)](../tabular-model-solutions-ssas-tabular.md)  
  
-   [Развертывание решений табличной модели (табличные службы SSAS)](../tabular-models/tabular-model-solution-deployment-ssas-tabular.md)  
  
-   [Соединение семантической модели бизнес-аналитики PowerPivot &#40;. BISM&#41;](../power-pivot-sharepoint/power-pivot-bi-semantic-model-connection-bism.md)  
  
 Схема CSDLBI создается сервером служб Analysis Services в ответ на запрос определения модели от клиентских средств, таких как [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]. Клиентское приложение отправляет XML-запрос серверу служб Analysis Services, на котором размещены данные модели. В ответ сервер отправляет XML-сообщение, содержащее определение сущностей в модели с использованием заметок CSDLBI. С помощью этих сведений клиентское средство создания отчетов представляет поля, статистические выражения и меры, доступные в модели. Заметки CSDLBI также содержат сведения о том, как группировать, сортировать и форматировать данные.  
  
 Общие сведения о CSDLBI см. в разделе [Основные понятия CSDLBI](/analysis-services/csdlbi/csdlbi-concepts).  
  
### <a name="working-with-csdl"></a>Работа с языком CSDL  
 Набор заметок CSDLBI, представляющий любую конкретную табличную модель, — это XML-документ, содержащий коллекцию сущностей, как простых, так и сложных. Сущности определяют таблицы (или измерения), столбцы (атрибуты), ассоциации (связи) и формулы, включенные в вычисляемые столбцы, меры и ключевые показатели эффективности.  
  
 Эти объекты нельзя изменять непосредственно, для их изменения следует использовать клиентские средства и API-интерфейсы для работы с табличными моделями.  
  
 CSDL-код для модели можно получить, отправив запрос DISCOVER на сервер, на котором размещается модель. Запрос следует уточнить, указав сервер и модель, а также при необходимости представление или перспективу. Возвращаемое сообщение является XML-строкой. Некоторые элементы зависят от языка и могут возвращать разные значения в зависимости от языка текущего соединения. Дополнительные сведения см. в разделе [DISCOVER_CSDL_METADATA набор строк](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-csdl-metadata-rowset).  
  
### <a name="csdlbi-versions"></a>Версии CSDLBI  
 Изначальная спецификация языка CSDL (для платформы Entity Data Framework) предоставляет большинство сущностей и свойств, необходимых для моделирования. Заметки бизнес-аналитики поддерживают особые требования табличных моделей, необходимые для клиентов (таких как [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]) свойства отчетов и дополнительные метаданные, необходимые для многомерных моделей. В этом разделе описаны изменения в каждой версии.  
  
 **CSDLBI 1.0**  
  
 Начальный набор добавлений в схему CSDL для поддержки табличных моделей [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] содержал заметки для поддержки моделирования данных, пользовательских вычислений и расширенного представления.  
  
-   Новые элементы и свойства для поддержки табличных моделей. Например, было добавлено свойство для указания типа запроса к базе данных, используемого для заполнения модели.  
  
-   Новые свойства и расширения существующих сущностей.  Например, элемент Association был расширен для поддержки связей.  
  
-   Свойства визуализации и навигации. Например, добавлены свойства для поддержки пользовательских полей сортировки, изображений по умолчанию и  
  
 **CSDLBI 1.1**  
  
 Эта версия схемы CSDLBI включает расширения для поддержки многомерных баз данных (таких как кубы OLAP). Новые элементы и свойства имеют следующий вид:  
  
-   Поддержка измерений как сущностей.  
  
-   Поддержка иерархий.  
  
-   Доступ к разделам ROLAP.  
  
-   Поддержка переводов.  
  
-   Поддержка перспектив.  
  
 Подробные сведения об отдельных элементах в заметках CSDLBI см. [в статье Технический справочник по аннотациям бизнес-аналитики на языке CSDL](/analysis-services/csdlbi/technical-reference-for-bi-annotations-to-csdl). Сведения о базовой спецификации языка CSDL см. в [спецификации CSDL v3](https://docs.microsoft.com/ef/ef6/modeling/designer/advanced/edmx/csdl-spec).  
  
  
## <a name="see-also"></a>См. также:  
 [Основные сведения об табличной модели объектов](representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)   
 [Основные понятия CSDLBI](/analysis-services/csdlbi/csdlbi-concepts)   
 [Основные сведения о табличной объектной модели](representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)  
  
  
