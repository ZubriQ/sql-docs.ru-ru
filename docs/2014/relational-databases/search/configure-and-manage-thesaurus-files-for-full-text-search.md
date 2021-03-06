---
title: Настройка файлов тезауруса для полнотекстового поиска и управление ими | Документация Майкрософт
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- full-text indexes [SQL Server], thesaurus files
- thesaurus [full-text search], configuring
- thesaurus [full-text search]
ms.assetid: 3ef96a63-8a52-45be-9a1f-265bff400e54
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: e52399dc77fce220bf33939b7c7921e32cd2438c
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66011478"
---
# <a name="configure-and-manage-thesaurus-files-for-full-text-search"></a>Настройка и управление файлами тезауруса для полнотекстового поиска
  В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]полнотекстовые запросы могут выполнять поиск синонимов для заданных пользователем терминов с помощью тезауруса. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ** определяет набор синонимов для указанного языка. Системные администраторы могут определить две формы синонимов: расширяющие наборы и заменяющие наборы. Подготовив тезаурус, ориентированный на пользовательские полнотекстовые данные, можно эффективно расширить область полнотекстовых запросов к этим данным. Сопоставление с тезаурусом выполняется для всех запросов [FREETEXT](/sql/t-sql/queries/freetext-transact-sql) и [FREETEXTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) и для любых запросов [CONTAINS](/sql/t-sql/queries/contains-transact-sql) и [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) , которые указывают предложение FORMSOF THESAURUS.  
  
##  <a name="basic-tasks-for-setting-up-a-thesaurus-file"></a><a name="tasks"></a>Основные задачи по настройке файла тезауруса  
 Прежде чем запросы полнотекстового поиска экземпляра сервера смогут найти синонимы на данном языке, необходимо определить сопоставления тезауруса (синонимы) для этого языка. В каждом тезаурусе необходимо вручную определить следующее.  
  
-   Настройка диакритических знаков  
  
     Для данного тезауруса все шаблоны поиска являются конфиденциальными или не чувствительны к диакритическим знакам, таким как тильда (**~**), знак ударения (**??**) или умляут (**??).** (т. е. с *учетом диакритических* знаков или *без учета диакритических*знаков). Например, предположим, что вы указали шаблон «каф??». другими шаблонами. Если тезаурус не учитывает диакритические знаки, полнотекстовый поиск заменит шаблоны "КАФ??" и "cafe". Если тезаурус учитывает диакритические знаки, полнотекстовый поиск заменяет только шаблон "КАФ??". По умолчанию тезаурус не учитывает диакритические знаки.  
  
-   Расширяющий набор  
  
     Расширяющий набор содержит группу синонимов, таких как «писатель», «автор» и «журналист», которые заменяют друг друга в полнотекстовом поиске. Запросы, содержащие слова, которые совпадают с одним из синонимов в расширяющем наборе, расширяются таким образом, чтобы включать в себя все другие синонимы в этом расширяющем наборе.  
  
     Дополнительные сведения см. в подразделе «XML-структура расширяющего набора» далее в этом разделе.  
  
-   Заменяющий набор  
  
     Заменяющий набор содержит текстовый шаблон, заменяемый подстановочным набором. Пример см. в подразделе «XML-структура заменяющего набора» далее в этом разделе.  
  
  
##  <a name="initial-content-of-the-thesaurus-files"></a><a name="initial_thesaurus_files"></a>Первоначальное содержимое файлов тезауруса  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предоставляет набор XML-файлов тезауруса, по одному для каждого поддерживаемого языка. Эти файлы в основном пустые. Они содержат только XML-структуру верхнего уровня, общую для всех тезаурусов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , и заключенный в комментарии образец тезауруса.  
  
 Все файлы тезауруса, поставляемые с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], содержат следующий XML-код:  
  
```  
<XML ID="Microsoft Search Thesaurus">  
  
<!--  Commented out  
  
    <thesaurus xmlns="x-schema:tsSchema.xml">  
<diacritics_sensitive>0</diacritics_sensitive>  
        <expansion>  
            <sub>Internet Explorer</sub>  
            <sub>IE</sub>  
            <sub>IE5</sub>  
        </expansion>  
        <replacement>  
            <pat>NT5</pat>  
            <pat>W2K</pat>  
            <sub>Windows 2012</sub>  
        </replacement>  
        <expansion>  
            <sub>run</sub>  
            <sub>jog</sub>  
        </expansion>  
    </thesaurus>  
-->  
</XML>  
```  
  
  
##  <a name="location-of-the-thesaurus-files"></a><a name="location"></a>Расположение файлов тезауруса  
 Местоположение файлов тезауруса по умолчанию:  
  
 *<SQL_Server_data_files_path>* \MSSQL12. мссклсервер\мсскл\фтдата\  
  
 В местоположении по умолчанию содержатся следующие файлы.  
  
-   Зависящие от языка файлы тезауруса  
  
     При установке в указанном выше месте устанавливаются пустые файлы тезауруса. Для каждого поддерживаемого языка предоставляется отдельный файл. Системный администратор может настроить эти файлы.  
  
     Имена файлов по умолчанию для файлов тезауруса имеют следующий формат:  
  
     "TS" + \<сокращенное обозначение языка> + ". XML"  
  
     Имя файла тезауруса для данного языка указывается в следующем параметре реестра: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<имя-экземпляра>\MSSearch\\<аббревиатура-языка>.  
  
-   Файл глобального тезауруса  
  
     Пустой файл глобального тезауруса, tsGlobal.xml.  
  
 Можно менять местонахождение и имена файлов тезауруса, изменяя соответствующий раздел реестра. Для каждого языка местонахождение файла тезауруса указывается в следующем параметре реестра:  
  
 HKLM/SOFTWARE/Microsoft/Microsoft SQL Server/\<имя экземпляра>/мссеарч/лангуаже/\<язык — аббревиатура>/тсаурусфиле  
  
 Файл глобального тезауруса соответствует языку «Нейтральный» с кодом языка (LCID) 0. Это значение может быть изменено только администратором.  
  
  
##  <a name="how-queries-use-thesaurus-files"></a><a name="how_queries_use_tf"></a>Использование файлов тезауруса в запросах  
 В каждом запросе тезауруса используется как языковой тезаурус, так и глобальный. Вначале запрос ищет файл, относящийся к конкретному языку, и загружает его для обработки (если он не загружен). Запрос расширяется с целью включить в файл тезауруса синонимы конкретного языка, заданные правилами расширяющего и заменяющего наборов. Затем эти шаги повторяются для глобального тезауруса. Но если термин уже входит в состав соответствий в файле конкретного языка, он используется в глобальном тезаурусе.  
  
  
##  <a name="understanding-the-structure-of-a-thesaurus-file"></a><a name="structure"></a>Основные сведения о структуре файла тезауруса  
 Каждый файл тезауруса определяет XML-контейнер, идентификатор которого — `Microsoft Search Thesaurus`, и комментарий, `<!--` ... `-->`, который содержит образец тезауруса. Тезаурус определяется в \<тезаурусе> элементе, который содержит примеры дочерних элементов, определяющих параметры диакритических знаков, расширяющие наборы и наборы для замены, следующим образом.  
  
-   XML-структура настройки диакритических знаков  
  
     Настройка диакритических знаков определяется в отдельном элементе <diacritics_sensitive>. Этот элемент содержит целое значение, которое управляет поведением диакритических знаков, как показано ниже.  
  
    |Настройка диакритических знаков|Применение|XML|  
    |------------------------|-----------|---------|  
    |без учета диакритических знаков|0|`<diacritics_sensitive>0</diacritics_sensitive>`|  
    |с учетом диакритических знаков|1|`<diacritics_sensitive>1</diacritics_sensitive>`|  
  
    > [!NOTE]  
    >  Эту настройку можно применить для файла только единожды, и она применяется для всех шаблонов поиска в файле. Этот параметр невозможно указать для отдельных шаблонов.  
  
-   XML-структура расширяющего набора  
  
     Каждый расширяющий набор заключается \<в элемент> расширения. В этом элементе вы указываете одну или несколько подстановок в \<элементе>. В расширяющем наборе можно указать группу подстановок, являющихся синонимами.  
  
     Например, можно изменить раздел расширения так, чтобы подстановки «писатель», «автор» и «журналист» считались синонимами. Полнотекстовые запросы, содержащие слова, совпадающие с одним из подстановочных слов, расширяются таким образом, чтобы включать в себя другие подстановочные слова в этом расширяющем наборе. Следовательно, в предыдущем примере при выполнении запроса FORMS OF THESAURUS или FREETEXT со словом «автор» после полнотекстового поиска будут также возвращены результаты, содержащие слова «писатель» и «журналист».  
  
     Для этого примера раздел расширяющего набора должен выглядеть следующим образом:  
  
    ```  
    <expansion>  
            <sub>writer</sub>  
            <sub>author</sub>  
            <sub>journalist</sub>  
    </expansion>  
    ```  
  
-   XML-структура заменяющего набора  
  
     Каждый заменяющий набор заключается в элемент> \<замены. В этом элементе можно указать один или несколько шаблонов в элементе \<Pat>, а также ноль или более подстановок в \<элементах под>, по одному на синоним. Можно указать шаблон, заменяемый подстановочным набором. Шаблоны и подстановки могут содержать одно слово или последовательность слов. Если для шаблона не указано подстановки, то шаблон удаляется из запроса пользователя.  
  
     Например, допустим, что необходимо заменить слово-шаблон «Win8» словами «Windows Server 2012» или «Windows 8.0». При выполнении полнотекстового запроса со словом «Win8» полнотекстовый поиск возвращает только результаты, содержащие слова «Windows Server 2012» или «Windows 8.0». Результаты, содержащие слово «Win8», не возвращаются. Это происходит потому, что шаблон «Win8» был заменен шаблонами «Windows Server 2012» и «Windows 8.0».  
  
     Для этого примера раздел заменяющего набора должен выглядеть следующим образом:  
  
    ```  
    <replacement>  
            <pat>Win8</pat>  
            <sub>Windows Server 2012</sub>  
            <sub>Windows 8.0</sub>  
    </replacement>  
    ```  
  
     Если имеются два заменяющих набора с одинаковыми сравниваемыми шаблонами, приоритет имеет самый длинный из них. Например, если определены следующие заменяющие наборы, при выполнении запроса FORMS OF THESAURUS по фразе «сообщество Internet Explorer в сети», набор «Internet Explorer» имеет приоритет перед набором «Internet». Следовательно, запрос будет обрабатываться так, как будто он сформирован по фразам «сообщество IE в сети» или «сообщество IE 9 в сети».  
  
    ```  
    <replacement>  
             <pat>Internet</pat>  
             <sub>intranet</sub>  
    </replacement>  
    ```  
  
     и  
  
    ```  
    <replacement>  
             <pat>Internet Explorer</pat>  
             <sub>IE</sub>  
             <sub>IE 9</sub>  
    </replacement>  
    ```  
  
  
##  <a name="working-with-thesaurus-files"></a><a name="working_with_thesaurus_files"></a>Работа с файлами тезауруса  
 **Изменение файла тезауруса**  
  
-   [Изменение файла тезауруса](#editing)  
  
 **Загрузка обновленного файла тезауруса**  
  
-   [sp_fulltext_load_thesaurus_file (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-fulltext-load-thesaurus-file-transact-sql)  
  
 **Просмотр разметки, полученной в результате применения средства разбиения по словам, тезауруса и списка стоп-слов**  
  
-   [sys. dm_fts_parser &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-parser-transact-sql)  
  
  
##  <a name="editing-a-thesaurus-file"></a><a name="editing"></a>Изменение файла тезауруса  
 Тезаурус для данного языка может быть настроен путем изменения соответствующего файла тезауруса (XML-файла). Во время установки пустые файлы тезауруса, содержащие только \<контейнер> XML, и образец \<тезауруса с комментарием> устанавливаются. Чтобы запросы полнотекстового поиска, которые ищут синонимы, работали правильно, необходимо создать фактический \<тезаурус> элемент, определяющий набор синонимов. Могут быть определены две формы синонимов — расширяющие наборы и заменяющие наборы.  
  
 **Ограничения для файлов тезауруса**  
  
 На изменения файла тезауруса налагаются следующие ограничения.  
  
-   Только системные администраторы имеют право обновлять, изменять и удалять файлы тезауруса.  
  
-   При изменении файлов тезауруса с помощью текстовых редакторов эти файлы необходимо сохранять в Юникоде с указанием отметок порядка байтов.  
  
-   Элементы тезауруса не могут быть пустыми или делиться на пустые строки.  
  
-   Фразы в файле тезауруса не могут иметь длину более 512 символов.  
  
-   Тезаурус не должен содержать повторяющихся записей между \<под>ными записями расширяющих наборов и элементами> \<Pat наборов замещения.  
  
 **Рекомендации для файлов тезауруса**  
  
 Рекомендуется, чтобы элементы в файле тезауруса не содержали специальных символов. Это объясняется особенностями поведения средств разбиения по словам в отношении специальных символов. Если элемент тезауруса содержит какие-нибудь специальные символы, то средства разбиения по словам, использованные в сочетании с этим элементом, могут оказать малозаметное воздействие на поведение полнотекстового запроса.  
  
 Рекомендуется, чтобы \<записи> не содержали стоп-слова, так как стоп-слова опущены в полнотекстовом индексе. Запросы разворачиваются для включения \<под> записей из файла тезауруса, и если запись \<вложенного> содержит стоп-слова, размер запроса увеличивается необязательно.  
  
#### <a name="to-edit-a-thesaurus-file"></a>Изменение файла тезауруса  
  
1.  Откройте файл тезауруса в Блокноте.  
  
2.  При первом редактировании файла тезауруса удалите следующие строки комментариев, находящиеся, соответственно, в конце и в начале файла:  
  
    ```  
    <!--Commented out  
    -->  
    ```  
  
3.  Добавьте, измените или удалите заменяющий или расширяющий набор.  
  
4.  Сохраните файл и закройте Блокнот.  
  
5.  Используйте хранимую процедуру [sp_fulltext_load_thesaurus_file](/sql/relational-databases/system-stored-procedures/sp-fulltext-load-thesaurus-file-transact-sql) , чтобы загрузить содержимое файла тезауруса в базу данных tempdb, указав идентификатор языкового стандарта (LCID), соответствующий языку файла тезауруса. Например, файлу тезауруса английского языка, tsenu.xml, соответствует код языка 1033.  
  
    ```  
    USE AdventureWorks2012 ;  
    EXEC sys.sp_fulltext_load_thesaurus_file 1033;  
    GO  
    ```  
  
  
## <a name="see-also"></a>См. также  
 [СОДЕРЖИТ &#40;&#41;Transact-SQL](/sql/t-sql/queries/contains-transact-sql)   
 [CONTAINSTABLE (Transact-SQL)](/sql/relational-databases/system-functions/containstable-transact-sql)   
 [FREETEXT (Transact-SQL)](/sql/t-sql/queries/freetext-transact-sql)   
 [FREETEXTTABLE (Transact-SQL)](/sql/relational-databases/system-functions/freetexttable-transact-sql)   
 [Полнотекстовый поиск](full-text-search.md)  
  
  
