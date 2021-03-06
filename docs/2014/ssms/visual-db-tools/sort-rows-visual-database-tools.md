---
title: Сортировка строк (визуальные инструменты для баз данных) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- sorting rows [SQL Server]
- sorting query results [SQL Server]
ms.assetid: 780ef467-f96e-4373-8235-6dacbedb05a2
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3235c9a9305e4476214add63f8710ba9de7b4c19
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "63049162"
---
# <a name="sort-rows-visual-database-tools"></a>Сортировка строк (визуальные инструменты для баз данных)
  Строки в результатах запроса можно сортировать. То есть можно указать конкретный столбец или набор столбцов, значениями которых определяется порядок строк в результирующем наборе.  
  
> [!NOTE]  
>  Порядок сортировки частично определяется параметрами сортировки столбца. Очередность использования параметров сортировки можно изменить в диалоговом окне [Параметры сортировки](visual-database-tools.md).  
  
 Существует несколько способов сортировки результатов запроса:  
  
-   **Можно упорядочивать строки по возрастанию или по убыванию.** По умолчанию SQL использует столбцы, по которым ведется упорядочение, для расположения строк в возрастающем порядке. Например, чтобы упорядочить наименования книг в порядке возрастания цен, достаточно отсортировать строки по столбцу цен. Конечный код SQL может выглядеть следующим образом:  
  
    ```  
    SELECT *  
    FROM titles  
    ORDER BY price  
  
    ```  
  
     С другой стороны, если нужно сортировать названия книг так, чтобы в начале списка были расположены самые дорогие, можно явно указать порядок, в котором первым располагается элемент с самым высоким значением. То есть указать, что строки результата должны быть упорядочены по убыванию значений в столбце цен. Конечный код SQL может выглядеть следующим образом:  
  
    ```  
    SELECT *  
    FROM titles  
    ORDER BY price DESC  
  
    ```  
  
-   **Можно сортировать по нескольким столбцам.** Например, можно создать результирующий набор, содержащий по одной строке для каждого автора, упорядоченный сначала по штату, затем по городу. Конечный код SQL может выглядеть следующим образом:  
  
    ```  
    SELECT *  
    FROM authors   
    ORDER BY state, city  
  
    ```  
  
-   **Можно сортировать по столбцам, не отображаемым в наборе результатов.** Например можно создать результирующий набор, в начале которого размещены самые дорогостоящие книги, хотя столбец цен при этом не отображается. Конечный код SQL может выглядеть следующим образом:  
  
    ```  
    SELECT title_id, title  
    FROM titles  
    ORDER BY price DESC  
  
    ```  
  
-   **Можно сортировать по производным столбцам.** Например, можно создать результирующий набор, каждая строка которого будет содержать наименование книги, причем первыми будут перечислены книги, авторы которых получают самый большой процент отчислений с проданного экземпляра. Конечный код SQL может выглядеть следующим образом:  
  
    ```  
    SELECT title, price * royalty / 100 as royalty_per_unit  
    FROM titles  
    ORDER BY royalty_per_unit DESC  
  
    ```  
  
     (Формула для вычисления авторского гонорара с проданного экземпляра каждой книги выделена.)  
  
     Чтобы вычислить производный столбец, можно использовать синтаксис SQL, как в предыдущем примере, или определяемую пользователем функцию, которая возвращает скалярное значение. Дополнительные сведения об определяемых пользователем функциях см. в документации по SQL Server.  
  
-   **Можно сортировать сгруппированные строки.** Например, можно создать результирующий набор, каждая строка которого будет описывать какой-либо город и указывать количество авторов из этого города, причем первыми будут перечислены города с большим числом авторов. Конечный код SQL может выглядеть следующим образом:  
  
    ```  
    SELECT city, state, COUNT(*)  
    FROM authors  
    GROUP BY city, state  
    ORDER BY COUNT(*) DESC, state  
  
    ```  
  
     Обратите внимание на то, что в запросе используется `state` в качестве второстепенного столбца сортировки. Таким образом, если в двух штатах имеется одинаковое количество авторов, эти штаты располагаются в алфавитном порядке.  
  
-   **Можно сортировать с использованием данных в разных языковых форматах** То есть можно сортировать столбец, используя соглашения о порядке сортировки, отличные от соглашений по умолчанию, применяемых для этого столбца. Например, можно написать запрос, получающий все заголовки книг с помощью Джэйми пати?? вывода. Чтобы отобразить наименования в алфавитном порядке, для столбца наименований используется испанская схема упорядочения. Конечный код SQL может выглядеть следующим образом:  
  
    ```  
    SELECT title  
    FROM   
        authors   
        INNER JOIN   
            titleauthor   
            ON authors.au_id   
            =  titleauthor.au_id   
            INNER JOIN  
                titles   
                ON titleauthor.title_id   
                =  titles.title_id   
    WHERE   
         au_fname = 'Jaime' AND   
         au_lname = 'Pati??o'  
    ORDER BY   
         title COLLATE SQL_Spanish_Pref_CP1_CI_AS  
    ```  
  
## <a name="see-also"></a>См. также:  
 [Сортировка и Группировка результатов запроса &#40;визуальных инструментов для баз данных&#41;](sort-and-group-query-results-visual-database-tools.md)   
 [Разделы по конструированию запросов и представлений (визуальные инструменты для баз данных)](design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
  
