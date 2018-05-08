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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eba265b727d00690ab77c6ae831e954d59df7c50
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugcontrollerhasqueuedcallbacks-method"></a>Método ICorDebugController::HasQueuedCallbacks
Obtém um valor que indica se qualquer retornos de chamada gerenciados atualmente na fila para o segmento especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT HasQueuedCallbacks (  
    [in] ICorDebugThread *pThread,  
    [out] BOOL           *pbQueued  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pThread`  
 [in] Um ponteiro para um objeto de "ICorDebugThread" que representa o thread.  
  
 `pbQueued`  
 [out] Um ponteiro para um valor que é `true` se qualquer retornos de chamada gerenciados estão atualmente na fila para o segmento especificado; caso contrário, `false`.  
  
 Se null for especificado para o `pThread` parâmetro `HasQueuedCallbacks` retornará `true` se há retornos de chamada gerenciados na fila de qualquer thread.  
  
## <a name="remarks"></a>Comentários  
 Retornos de chamada será expedida um por vez, cada vez que [Icordebugcontroller](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) é chamado. O depurador pode verificar esse sinalizador se deseja relatar vários eventos de depuração que ocorrem simultaneamente.  
  
 Quando eventos de depuração são enfileirados, eles já tenham ocorrido, para que o depurador deve esvaziar a fila inteira para ter certeza do estado do elemento a ser depurado. (Chamar `ICorDebugController::Continue` para que a fila.) Por exemplo, se a fila contém dois eventos de depuração no thread *X*, e o depurador suspende a thread *X* após o primeiro evento de depuração e, em seguida, chama `ICorDebugController::Continue`, o segundo evento de depuração para thread *X* será enviado, embora o thread foi suspenso.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 
