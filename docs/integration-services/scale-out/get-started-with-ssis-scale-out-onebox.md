---
title: Начало работы с развертыванием SSIS с горизонтальным увеличением масштаба на одном компьютере | Документы Майкрософт
description: В этой статье приводятся все сведения, необходимые для того, чтобы начать работу с развертыванием SSIS с горизонтальным увеличением масштаба.
ms.custom: performance
ms.date: 12/13/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: maghan
ms.technology: integration-services
ms.topic: conceptual
author: haoqian
ms.author: haoqian
ms.openlocfilehash: a2d6929277b7d024e45daaefd5cb41dccd495c63
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "68082162"
---
# <a name="get-started-with-integration-services-ssis-scale-out-on-a-single-computer"></a>Начало работы с развертыванием SSIS с горизонтальным увеличением масштаба на одном компьютере

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


В этом разделе приводятся рекомендации по настройке горизонтального увеличения масштаба Integration Services в среде с одним компьютером с параметрами по умолчанию.

## <a name="1-install-sql-server-features"></a>1. Установка компонентов SQL Server
В мастере SQL Server на странице **Выбор компонентов** выберите следующие элементы:
-   Службы ядра СУБД
-   Службы Integration Services
    -   Мастер горизонтального увеличения масштаба
    -   Рабочая роль горизонтального увеличения масштаба

![Первая половина списка на странице "Выбор компонентов"](media/feature-select-onebox1.PNG)

![Вторая половина списка на странице "Выбор компонентов"](media/feature-select-onebox2.PNG)

На странице **Конфигурация сервера** нажмите кнопку **Далее**, чтобы принять учетные записи служб и типы запуска по умолчанию.

На странице **Настройка ядра СУБД** установите переключатель в положение **Смешанный режим** и нажмите кнопку **Добавить текущего пользователя**. 

![Настройка ядра СУБД](media/engine-config.PNG)

На страницах **Настройка развертывания служб Integration Services с горизонтальным увеличением масштаба — главный узел** и **Настройка развертывания служб Integration Services с горизонтальным увеличением масштаба — рабочий узел** нажмите кнопку **Далее**, чтобы применить параметры по умолчанию для порта и сертификатов.

Завершите работу мастера установки SQL Server.

## <a name="2-install-sql-server-management-studio"></a>2. Установите SQL Server Management Studio

Скачайте и установите [SQL Server Management Studio (SSMS)](../../ssms/download-sql-server-management-studio-ssms.md).

## <a name="3-enable-scale-out"></a>3. Включение горизонтального увеличения масштаба
Откройте среду SQL Server Management Studio и подключитесь к локальному экземпляру SQL Server.
В обозревателе объектов щелкните правой кнопкой мыши узел **Каталоги служб Integration Services** и выберите пункт **Создать каталог**.

В диалоговом окне **Создать каталог** параметр **Включить этот сервер в качестве мастера горизонтального увеличения масштаба SSIS** выбран по умолчанию.

## <a name="4-enable-a-scale-out-worker"></a>4. Включение рабочей роли горизонтального увеличения масштаба
В SQL Server Management Studio (SSMS) щелкните правой кнопкой мыши элемент **SSISDB** и выберите пункт **Управление горизонтальным увеличением масштаба**. 

![Управление развертыванием с горизонтальным увеличением масштаба](media/manage-scale-out.PNG)

Откроется диспетчер горизонтального увеличения масштаба Integration Services. Дополнительные сведения см. в разделе [Диспетчер горизонтального увеличения масштаба](integration-services-ssis-scale-out-manager.md).

Чтобы включить рабочую роль горизонтального увеличения масштаба, перейдите в **диспетчер рабочих ролей** и выберите рабочую роль, которую нужно включить. Рабочие роли по умолчанию отключены. Чтобы включить выбранную рабочую роль, щелкните **Включить рабочую роль**.

## <a name="5-run-packages-in-scale-out"></a>5. Выполнение пакетов в развертывании с горизонтальным увеличением масштаба
Теперь пакеты служб SSIS можно запускать в развертывании с горизонтальным увеличением масштаба. Дополнительные сведения см. в статье [Выполнение пакетов в развертывании с горизонтальным увеличением масштаба служб Integration Services (SSIS)](run-packages-in-integration-services-ssis-scale-out.md).

## <a name="next-steps"></a>Дальнейшие действия
-   [Добавление рабочей роли горизонтального увеличения масштаба с помощью диспетчера горизонтального увеличения масштаба](add-scale-out-worker.md)
