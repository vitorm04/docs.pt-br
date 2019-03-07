---
title: Método ICorDebugController::SetAllThreadsDebugState
ms.date: 03/30/2017
api_name:
- ICorDebugController.SetAllThreadsDebugState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::SetAllThreadsDebugState
helpviewer_keywords:
- SetAllThreadsDebugState method [.NET Framework debugging]
- ICorDebugController::SetAllThreadsDebugState method [.NET Framework debugging]
ms.assetid: bdda4bd7-4743-4d58-a22b-8067e967db95
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0dffe95df75fafe293c225c513db7ff7896765fa
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57501767"
---
# <a name="icordebugcontrollersetallthreadsdebugstate-method"></a>Método ICorDebugController::SetAllThreadsDebugState
Define o estado de depuração de todos os threads gerenciados no processo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT SetAllThreadsDebugState (  
    [in] CorDebugThreadState  state,  
    [in] ICorDebugThread      *pExceptThisThread  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `state`  
 [in] Um valor de enumeração "CorDebugThreadState" que especifica o estado do thread para depuração.  
  
 `pExceptThisThread`  
 [in] Um ponteiro para um objeto de "ICorDebugThread" que representa um thread para ser isentos da configuração de estado de depuração. Se esse valor for nulo, nenhum thread é isento.  
  
## <a name="remarks"></a>Comentários  
 O `SetAllThreadsDebugState` método pode afetar os threads que não estão visíveis por meio [método EnumerateThreads](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md), então threads que foram suspensos com o `SetAllThreadsDebugState` método precisará ser retomada, com o `SetAllThreadsDebugState` método.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

