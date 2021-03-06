---
title: Занятие 6. Использование параметров в модели развертывания проекта | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 9216f18c-1762-4f2d-8c22-bd0ab7107555
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: d559defe1dd08f26077738cdd0aea219e8f7554b
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "62890549"
---
# <a name="lesson-6-using-parameters-with-the-project-deployment-model"></a>Занятие 6: Использование параметров в модели развертывания проекта
  В SQL Server 2012 была добавлена новая модель развертывания, позволяющая развертывать проекты на сервере служб Integration Services. Сервер служб Integration Services позволяет управлять пакетами, запускать пакеты, а также настраивать значения времени выполнения для пакетов.  
  
 На этом занятии будет изменен пакет, созданный на [занятии 5. Добавление конфигураций пакетов для модели развертывания пакетов](lesson-5-add-ssis-package-configurations-for-the-package-deployment-model.md) для использования модели развертывания проекта. Значение конфигурации будет заменено на параметр, чтобы указать местоположение образцов данных. Также можно скопировать пакет завершенного урока 5, который включен в учебник.  
  
 С использованием мастера настройки проекта служб Integration Services будет выполнено преобразование проекта для использования модели развертывания проектов, а также использования параметра, а не значения конфигурации для задания свойства каталога. На этом занятии частично рассматриваются шаги, необходимые для преобразования существующих пакетов служб SSIS в новую модель развертывания проекта.  
  
 При повторном выполнении пакета служба Integration Services использует параметр для заполнения значения переменной, а переменная в свою очередь обновит свойство "Каталог". В итоге пакет последовательно проходит все файлы в новой папке данных, определенной значением параметра, а не в папке, заданной в файле конфигурации пакета.  
  
> [!IMPORTANT]  
>  Для выполнения упражнений этого учебника потребуется образец базы данных **AdventureWorksDW2012** . Дополнительные сведения об установке и развертывании образца базы данных **AdventureWorksDW2012**см. в разделе [Вопросы установки образцов кода и образцов баз данных SQL Server](https://technet.microsoft.com/library/ms161556%28v=sql.105%29).  
  
## <a name="lesson-tasks"></a>Задачи занятия  
 Это занятие содержит следующие задачи.  
  
1.  [Шаг 1. Копирование пакета занятия 5](lesson-6-1-copying-the-lesson-5-package.md)  
  
2.  [Этап 2. Преобразование проекта в модель развертывания проекта](lesson-6-2-converting-the-project-to-the-project-deployment-model.md)  
  
3.  [Шаг 3. Проверка пакета, созданного на занятии 6](lesson-6-3-testing-the-lesson-6-package.md)  
  
4.  [Шаг 4. Развертывание пакета, созданного на занятии 6](lesson-6-4-deploying-the-lesson-6-package.md)  
  
## <a name="start-the-lesson"></a>Начало занятия  
 [Шаг 1. Копирование пакета занятия 5](lesson-6-1-copying-the-lesson-5-package.md)  
  
  
