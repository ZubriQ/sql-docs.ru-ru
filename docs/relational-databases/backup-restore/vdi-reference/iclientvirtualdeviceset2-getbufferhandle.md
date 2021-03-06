---
title: IClientVirtualDeviceSet2::GetBufferHandle
titlesuffix: SQL Server VDI reference
description: В этой статье приводятся справочные сведения о команде IClientVirtualDeviceSet2::GetBufferHandle.
ms.date: 08/30/2019
ms.prod: sql
ms.prod_service: backup-restore
ms.technology: backup-restore
ms.topic: reference
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 844ddad21eaf3fb579d6a0981f2a042238e92372
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "70847335"
---
# <a name="iclientvirtualdeviceset2getbufferhandle-vdi"></a>IClientVirtualDeviceSet2::GetBufferHandle (VDI)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Для работы с буферами, возвращаемыми функцией **IClientVirtualDevice2::GetCommand**, некоторым приложениям может требоваться несколько процессов. В таких случаях процесс, который получает команду, может использовать **GetBufferHandle** для получения независимого от процесса дескриптора, определяющего буфер. Затем этот дескриптор можно передать в любой другой процесс, где открыт тот же набор виртуальных устройств. Этот процесс будет использовать функцию IClientVirtualDeviceSet2::MapBufferHandle для получения адреса буфера. Скорее всего, адрес будет отличаться от адреса в партнерском процессе, так как каждый процесс может сопоставлять буферы по разным адресам.

## <a name="syntax"></a>Синтаксис

```c
HRESULT IClientVirtualDeviceSet2::GetBufferHandle (
   BYTE*         pBuffer,
   DWORD*      pBufferHandle
);
```

## <a name="parameters"></a>Параметры

*pBuffer* — адрес буфера, полученный в результате выполнения команды чтения или записи.

*pBufferHandle* — возвращается уникальный идентификатор буфера.

## <a name="return-value"></a>Возвращаемое значение

|Возвращаемое значение | Объяснение |
|---|---|
| NOERROR | Функция выполнена успешно. |
| VD_E_PROTOCOL | Набор виртуальных устройств в настоящее время не открыт. |
| VD_E_INVALID | pBuffer не является допустимым адресом. |

## <a name="remarks"></a>Remarks

Процесс, вызывающий функцию GetBufferHandle, отвечает за вызов IClientVirtualDevice2::CompleteCommand по завершении передачи данных.

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения см. в [справке по интерфейсу виртуальных устройств SQL Server](reference-virtual-device-interface.md).