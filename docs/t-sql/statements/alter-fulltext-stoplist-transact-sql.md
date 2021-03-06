---
title: ALTER FULLTEXT STOPLIST (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ALTER FULLTEXT STOPLIST
- ALTER_FULLTEXT_STOPLIST_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- stoplists [full-text search]
- full-text search [SQL Server], stoplists
- ALTER FULLTEXT STOPLIST statement
- full-text search [SQL Server], stopwords
- stopwords [full-text search]
ms.assetid: f6ad87d5-6a34-435a-8456-8244947c5c83
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 692f62c6a5b9d6268a27de350a860c0cb58c74bc
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "68067553"
---
# <a name="alter-fulltext-stoplist-transact-sql"></a>ALTER FULLTEXT STOPLIST (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Вставляет или удаляет стоп-слово в используемый по умолчанию полнотекстовый список стоп-слов текущей базы данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
ALTER FULLTEXT STOPLIST stoplist_name  
{   
        ADD [N] 'stopword' LANGUAGE language_term    
  | DROP   
    {  
        'stopword' LANGUAGE language_term   
      | ALL LANGUAGE language_term   
      | ALL  
     }  
;  
```  
  
## <a name="arguments"></a>Аргументы  
 *stoplist_name*  
 Имя изменяемого списка стоп-слов. Длина *stoplist_name* не может превышать 128 символов.  
  
 **'** *stopword* **'**  
 Строка, которая может быть словом с лингвистическим значением в определенном языке или токеном, не имеющим лингвистического значения. Длина *stopword* ограничена максимальной длиной токена (64 символами). Стоп-слово можно указать в виде строки в Юникоде.  
  
 LANGUAGE *language_term*  
 Указывает язык, связанный с добавляемым или удаляемым *stopword*.  
  
 Аргумент *language_term* может быть указан как строка, целое или шестнадцатеричное значение, соответствующее коду локали (LCID) следующим образом.  
  
|Формат|Description|  
|------------|-----------------|  
|String|Аргумент *language_term* соответствует значению столбца **alias** в представлении совместимости [sys.syslanguages (Transact-SQL)](../../relational-databases/system-compatibility-views/sys-syslanguages-transact-sql.md). Строка должна быть заключена в одиночные кавычки: **'***language_term***'** .|  
|Целое число|Аргумент *language_term* представляет собой код языка.|  
|Шестнадцатеричный|Аргумент *language_term* состоит из 0x со следующим шестнадцатеричным значением кода языка. Шестнадцатеричное значение не может иметь более восьми знаков, включая начальные нули. Если значение указано в формате двухбайтовой кодировки (DBCS), SQL Server преобразует его в Юникод.|  
  
 ADD **'***stopword***'** LANGUAGE *language_term*  
 Добавляет стоп-слово в список стоп-слов для языка, указанного в аргументе LANGUAGE *language_term*.  
  
 Если указанное сочетание ключевого слова и значения кода языка в рамках данного списка стоп-слов не уникальны, возвращается ошибка.  Если значение кода языка не соответствует зарегистрированному языку, формируется ошибка.  
  
 DROP { **'***stopword***'** LANGUAGE *language_term* | ALL LANGUAGE *language_term* | ALL }  
 Удаляет стоп-слово из списка стоп-слов.  
  
 **'** *stopword* **'** LANGUAGE *language_term*  
 Удаляет указанное стоп-слово для языка, указанного аргументом *language_term*.  
  
 ALL LANGUAGE *language_term*  
 Удаляет все стоп-слова для языка, указанного аргументом *language_term*.  
  
 ALL  
 Удаляет все стоп-слова из списка стоп-слов.  
  
## <a name="remarks"></a>Remarks  
 Инструкция CREATE FULLTEXT STOPLIST поддерживается только для уровня совместимости 100 и выше. Для уровней совместимости 80 и 90 системный список стоп-слов всегда назначается базе данных.  
  
## <a name="permissions"></a>Разрешения  
 Чтобы назначить список стоп-слов в качестве используемого по умолчанию списка стоп-слов базы данных, необходимо разрешение ALTER DATABASE. Чтобы изменить список стоп-слов другим образом, необходимо быть его владельцем или членом предопределенных ролей базы данных **db_owner** или **db_ddladmin**.  
  
## <a name="examples"></a>Примеры  
 В следующем примере демонстрируется изменение списка стоп-слов `CombinedFunctionWordList` путем добавления слова "en" для испанского и затем французского языков.  
  
```  
ALTER FULLTEXT STOPLIST CombinedFunctionWordList ADD 'en' LANGUAGE 'Spanish';  
ALTER FULLTEXT STOPLIST CombinedFunctionWordList ADD 'en' LANGUAGE 'French';  
```  
  
## <a name="see-also"></a>См. также:  
 [CREATE FULLTEXT STOPLIST (Transact-SQL)](../../t-sql/statements/create-fulltext-stoplist-transact-sql.md)   
 [DROP FULLTEXT STOPLIST (Transact-SQL)](../../t-sql/statements/drop-fulltext-stoplist-transact-sql.md)   
 [Настройка стоп-слов, списков стоп-слов и управление ими для полнотекстового поиска](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)   
 [sys.fulltext_stoplists (Transact-SQL)](../../relational-databases/system-catalog-views/sys-fulltext-stoplists-transact-sql.md)   
 [sys.fulltext_stopwords (Transact-SQL)](../../relational-databases/system-catalog-views/sys-fulltext-stopwords-transact-sql.md)   
 [Настройка стоп-слов, списков стоп-слов и управление ими для полнотекстового поиска](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)  
  
  
