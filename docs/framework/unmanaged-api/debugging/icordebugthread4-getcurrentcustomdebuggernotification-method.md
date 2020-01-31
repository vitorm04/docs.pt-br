---
title: Método ICorDebugThread4::GetCurrentCustomDebuggerNotification
ms.date: 03/30/2017
api_name:
- ICorDebugThread4.GetCurrentCustomDebuggerNotification Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread4::GetCurrentCustomDebuggerNotification
helpviewer_keywords:
- GetCurrentCustomDebuggerNotification method [.NET Framework debugging]
- ICorDebugThread4::GetCurrentCustomDebuggerNotification method [.NET Framework debugging]
ms.assetid: 57e0f2d2-5f0e-4e2d-99ec-3f26632eb693
topic_type:
- apiref
ms.openlocfilehash: a8a377074ca1005ad8089dfd8e2a6a464bb86f60
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791361"
---
# <a name="icordebugthread4getcurrentcustomdebuggernotification-method"></a>Método ICorDebugThread4::GetCurrentCustomDebuggerNotification

Obtém o objeto [ICorDebugManagedCallback3:: CustomNotification](icordebugmanagedcallback3-customnotification-method.md) atual no thread atual.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetCurrentCustomDebuggerNotification(
    [out] ICorDebugValue **ppNotificationObject
    );
```

## <a name="parameters"></a>Parâmetros

`ppNotificationObject`\
fora Um ponteiro para o objeto de `ICorDebugManagedCallback3::CustomNotification` atual no thread atual.

## <a name="remarks"></a>Comentários

O valor de `ppNotificationObject` será nulo se o método não for chamado de dentro de um retorno de chamada `ICorDebugManagedCallback3::CustomNotification` ou se não existir nenhum objeto de notificação atual.

## <a name="requirements"></a>Requisitos do

**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).

**Cabeçalho:** CorDebug.idl, CorDebug.h

**Biblioteca:** CorGuids.lib

**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]

## <a name="see-also"></a>Veja também

- [Interface ICorDebugThread4](icordebugthread4-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
- [Depuração](index.md)
