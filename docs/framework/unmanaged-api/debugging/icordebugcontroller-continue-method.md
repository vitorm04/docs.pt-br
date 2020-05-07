---
title: Método ICorDebugController::Continue
ms.date: 03/30/2017
api_name:
- ICorDebugController.Continue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Continue
helpviewer_keywords:
- Continue method [.NET Framework debugging]
- ICorDebugController::Continue method [.NET Framework debugging]
ms.assetid: 8684cd06-ad3e-48ef-832e-15320e1f43a2
topic_type:
- apiref
ms.openlocfilehash: 0fd7dfc1a48e21abbc80692c110bee55beb68e6b
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82892858"
---
# <a name="icordebugcontrollercontinue-method"></a>Método ICorDebugController::Continue

Retoma a execução de threads gerenciados após uma chamada para o [método Stop](icordebugcontroller-stop-method.md).

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT Continue (
    [in] BOOL fIsOutOfBand
);
```

## <a name="parameters"></a>Parâmetros

`fIsOutOfBand`  
no Defina como `true` se estiver continuando com um evento fora de banda; caso contrário, defina `false`como.

## <a name="remarks"></a>Comentários

`Continue`continua o processo após uma chamada para o `ICorDebugController::Stop` método.

Ao fazer a depuração de modo misto, não chame `Continue` no thread de eventos do Win32, a menos que você esteja continuando de um evento fora de banda.

Um *evento em banda* é um evento gerenciado ou um evento não gerenciado normal durante o qual o depurador dá suporte à interação com o estado gerenciado do processo. Nesse caso, o depurador recebe o retorno de chamada [ICorDebugUnmanagedCallback::D ebugevent](icordebugunmanagedcallback-debugevent-method.md) com `fOutOfBand` seu parâmetro definido `false`como.

Um *evento fora de banda* é um evento não gerenciado durante o qual a interação com o estado gerenciado do processo é impossível enquanto o processo é interrompido devido ao evento. Nesse caso, o depurador recebe o retorno `ICorDebugUnmanagedCallback::DebugEvent` de chamada com `fOutOfBand` seu parâmetro definido `true`como.

## <a name="requirements"></a>Requisitos

**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).

**Cabeçalho:** CorDebug.idl, CorDebug.h

**Biblioteca:** CorGuids.lib

**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
