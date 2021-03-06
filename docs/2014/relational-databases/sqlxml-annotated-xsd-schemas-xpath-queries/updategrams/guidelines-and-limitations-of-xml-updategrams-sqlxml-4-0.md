---
title: Рекомендации и ограничения XML диаграмм обновления (SQLXML 4,0) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- updategrams [SQLXML], about updategrams
ms.assetid: b5231859-14e2-4276-bc17-db2817b6f235
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 953fc5b7c203faa8fa6a9820993a3d0fd7a7de40
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66014830"
---
# <a name="guidelines-and-limitations-of-xml-updategrams-sqlxml-40"></a>Правила и ограничения диаграмм обновления XML (SQLXML 4.0)
  При использовании диаграмм обновления XML следует помнить следующее.  
  
-   Если вы используете диаграмма обновления для операции вставки с одной парой ** \<до>** и ** \<после блоков>** , то ** \<блок Before>** можно опустить. И наоборот, в случае операции удаления блок ** \<After>** можно опустить.  
  
-   Если вы используете диаграмма обновления с несколькими ** \<>** и ** \<после>ных** блоков в теге ** \<>синхронизации** , ** \<перед** ** \<>** и ** \<после**>ных пар необходимо ** \<** указать оба блока>и After>.  
  
-   Обновления в диаграммах обновления применяются к XML-представлению, предоставленному схемой XML. Поэтому для успешного сопоставления по умолчанию следует либо указать имя файла схемы в диаграмме обновления, либо, если имя файла не указано, имена элемента и атрибута должны совпадать с именами таблицы и столбца базы данных.  
  
-   SQLXML 4.0 требует, чтобы все значения столбцов в диаграмме обновления были бы явно сопоставлены в схеме (XDR или XSD), предоставленной для создания XML-представления для дочерних элементов. Такое поведение отличается от более ранних версий SQLXML, которые допускали отсутствие сопоставления для значения столбца в схеме, если оно являлось частью внешнего ключа заметки `sql:relationship`. (Следует отметить, что подобное изменение не повлияет на распространение значений первичного ключа на дочерние элементы, которое по-прежнему происходит в SQLXML 4.0, если явно не указано значение для дочернего элемента.  
  
-   Если вы используете диаграмма обновления для изменения данных в двоичном столбце (например [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] `image` , [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] тип данных), необходимо указать схему сопоставления, в которой должен быть указан тип данных (например, `sql:datatype="image"`) и тип данных XML (например, `dt:type="binhex"` или `dt:type="binbase64`). Данные для двоичного столбца должны быть указаны в диаграмме обновления; заметка `sql:url-encode`, указанная в схеме сопоставления, не учитывается в диаграмме обновления.  
  
-   Если при написании схемы XSD указываемое для заметки `sql:relation` или `sql:field` значение включает в себя специальный символ, такой как символ пробела (например, в имени таблицы «Order Details»), это значение должно быть заключено в скобки (например, «[Order Details]»).  
  
-   При использовании диаграмм обновления цепочки связей не поддерживаются. Например, если таблицы А и С связаны через цепочку связей, которая использует таблицу В, при попытке запустить и выполнить диаграмму обновления возникнет следующая ошибка:  
  
    ```  
    There is an inconsistency in the schema provided.  
    ```  
  
     Даже если как схема, так и диаграмма обновления верны и правильно оформлены, эта ошибка возникнет, если имеется цепочка связей.  
  
-   Диаграммы обновления не допускают передачи данных типа `image` как параметров в процессе обновления.  
  
-   Типы больших двоичных объектов (BLOB) `text/ntext` , такие как и Images, не следует использовать в блоке ** \<Before>** в при работе с диаграмм обновления, так как в этом случае они будут включены в управление параллелизмом. Это может вызвать проблемы в работе [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] из-за ограничений, налагаемых на сравнение для типов больших двоичных объектов. Например, ключевое слово LIKE используется в предложении WHERE для сравнения столбцов типа данных `text`; однако, в случае с типами больших двоичных объектов, когда размер данных превышает 8 КБ, такое сравнение завершится ошибкой.  
  
-   Специальные символы в данных типа `ntext` могут вызывать проблемы в работе SQLXML 4.0 из-за ограничений, налагаемых на сравнение типов больших двоичных объектов. Например, использование "[Serializable]" в блоке ** \<Before>** диаграмм обновления при использовании в проверке параллелизма столбца `ntext` типа приведет к сбою со следующим описанием ошибки SQLOLEDB:  
  
    ```  
    Empty update, no updatable rows found   Transaction aborted  
    ```  
  
## <a name="see-also"></a>См. также  
 [Вопросы безопасности диаграмма обновления &#40;SQLXML 4,0&#41;](../security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
