---
title: Создание политики имен для базы данных Finance | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 56b2c852-fd69-4cd2-9b5d-977467b94fd9
caps.latest.revision: 26
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: b16fd6b9ce9d89a730f64c5cadd7a67553cb6dd1
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37166915"
---
# <a name="create-the-finance-name-policy"></a>Создание политики имен финансов
  В этой задаче создается база данных с именем Finance, а затем формируется условие, требующее, чтобы все таблицы начинались с букв **fintbl**. После этого создается политика и категория политики по обеспечению стандарта именования таблиц в базе данных Finance.  
  
### <a name="to-create-the-finance-database"></a>Создание базы данных Finance  
  
1.  В среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]откройте окно запросов и выполните следующую инструкцию:  
  
    ```  
    CREATE DATABASE Finance ;  
    GO  
    ```  
  
2.  В обозревателе объектов щелкните **Базы данных**и нажмите клавишу F5 для обновления списка баз данных.  
  
### <a name="to-create-the-finance-tables-condition"></a>Создание условия «Таблицы Finance»  
  
1.  В обозревателе объектов раскройте узлы **Управление**и **Управление политиками**, щелкните правой кнопкой мыши узел **Условия**и выберите пункт **Создать условие**.  
  
2.  В диалоговом окне **Создание нового условия** в поле **Имя** введите **Finance Tables**.  
  
3.  В списке **Аспект** выберите **Многокомпонентное имя**.  
  
4.  В диалоговом окне **Выражение** поля **Поле** выберите **@Name**, в поле **Оператор** выберите **Like**, а в поле **Значение** введите **'fintbl%'** для того, чтобы все имена таблиц начинались с букв **fintbl**.  
  
5.  На странице **Описание** введите **Имена таблиц Finance должны начинаться с букв "fintbl"**, а затем нажмите кнопку **ОК** для создания условия.  
  
### <a name="to-create-the-finance-name-policy"></a>Создание политики имен Finance  
  
1.  В обозревателе объектов щелкните правой кнопкой мыши папку **Политики**и выберите в контекстном меню пункт **Создать политику**.  
  
2.  В диалоговом окне **Создание новой политики** в поле **Имя** введите **Finance Name**.  
  
3.  В списке **Проверить условия** выберите пункт **Таблицы Finance**. Он находится в области **Многокомпонентное имя** .  
  
4.  В области **Применить к** отображается список объектов баз данных, к которым можно применить эту политику. Установите флажок **Каждая таблица**.  
  
5.  В области **Каждая база данных** разверните раздел **Каждый**и нажмите **Создать условие**.  
  
6.  В диалоговом окне **Создание нового условия** в поле **Имя** введите **База данных Finance**.  
  
7.  В окне **Выражение** добавьте в выражение строку **@Name = 'Finance'** и нажмите кнопку **ОК**, чтобы закрыть страницу условия.  
  
    > [!NOTE]  
    >  Возможно, потребуется выйти из поля **Значение** для включения кнопки **ОК** .  
  
8.  В списке **Режим оценки** выберите **При изменении: запретить**. Это обеспечит создание политикой триггера базы данных в базе данных Finance.  
  
9. Установите флажок **Включено** . (Флажок **Включено** не применяется к политикам **По запросу** .)  
  
10. В списке **Ограничение сервера** выберите пункт **Нет**.  
  
11. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-create-the-finance-policy-category"></a>Создание категории политики Finance  
  
1.  В обозревателе объектов разверните узел **Управление**, щелкните правой кнопкой мыши узел **Управление политиками**и выберите пункт **Управление категориями**.  
  
2.  В **Управление категориями политик** диалогового **имя**, тип `Finance` в пустое поле, а затем снимите **обязательные подписки базы данных**. Параметр**Сделать подписки базы данных обязательными** принудительно подписывает каждую базу данных в экземпляре на политики, которые относятся к данной категории политик. В рамках этого занятия только база данных Finance должна быть подписана на политику "Finance Name".  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="next-task-in-lesson"></a>Следующая задача занятия  
 [Подписка на политику имен финансов и ее проверка](lesson-2-2-subscribe-to-and-check-the-finance-name-policy.md)  
  
  