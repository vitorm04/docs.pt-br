---
title: Método ICorDebugController::HasQueuedCallbacks
ms.date: 03/30/2017
api_name:
- ICorDebugController.HasQueuedCallbacks
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::HasQueuedCallbacks
helpviewer_keywords:
- HasQueuedCallbacks method [.NET Framework debugging]
- ICorDebugController::HasQueuedCallbacks method [.NET Framework debugging]
ms.assetid: 0d6a1cd9-370b-4462-adbf-e3980e897ea7
topic_type:
- apiref
ms.openlocfilehash: 51ee8b3631bffe9fd7fef4351e0aa67d1cbbe2c9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125395"
---
# <a name="icordebugcontrollerhasqueuedcallbacks-method"></a>Método ICorDebugController::HasQueuedCallbacks
Obtém um valor que indica se qualquer retorno de chamada gerenciado está na fila no momento para o thread especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT HasQueuedCallbacks (  
    [in] ICorDebugThread *pThread,  
    [out] BOOL           *pbQueued  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pThread`  
 no Um ponteiro para um objeto "ICorDebugThread" que representa o thread.  
  
 `pbQueued`  
 fora Um ponteiro para um valor `true` se algum retorno de chamada gerenciado estiver na fila no momento para o thread especificado; caso contrário, `false`.  
  
 Se NULL for especificado para o parâmetro `pThread`, `HasQueuedCallbacks` retornará `true` se houver retornos de chamada atualmente gerenciados na fila para qualquer thread.  
  
## <a name="remarks"></a>Comentários  
 Os retornos de chamada serão expedidos um de cada vez, sempre que [ICorDebugController:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) for chamado. O depurador pode verificar esse sinalizador se desejar relatar vários eventos de depuração que ocorrem simultaneamente.  
  
 Quando os eventos de depuração são enfileirados, eles já ocorreram, portanto, o depurador deve drenar toda a fila para ter certeza do estado do depurado. (Chame `ICorDebugController::Continue` para drenar a fila.) Por exemplo, se a fila contiver dois eventos de depuração no thread *x*, e o depurador suspender o thread *x* após o primeiro evento de depuração e, em seguida, chamar `ICorDebugController::Continue`, o segundo evento de depuração para o thread *x* será expedido, embora o o thread foi suspenso.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
