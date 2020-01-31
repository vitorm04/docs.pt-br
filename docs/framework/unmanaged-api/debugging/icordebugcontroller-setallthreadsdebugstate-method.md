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
ms.openlocfilehash: be7fce700756d7120e0853446b7b307ec77c2080
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76783767"
---
# <a name="icordebugcontrollersetallthreadsdebugstate-method"></a>Método ICorDebugController::SetAllThreadsDebugState
Define o estado de depuração de todos os threads gerenciados no processo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetAllThreadsDebugState (  
    [in] CorDebugThreadState  state,  
    [in] ICorDebugThread      *pExceptThisThread  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `state`  
 no Um valor da enumeração "CorDebugThreadState" que especifica o estado do thread para depuração.  
  
 `pExceptThisThread`  
 no Um ponteiro para um objeto "ICorDebugThread" que representa um thread a ser isento da configuração de estado de depuração. Se esse valor for NULL, nenhum thread será isento.  
  
## <a name="remarks"></a>Comentários  
 O método `SetAllThreadsDebugState` pode afetar os threads que não são visíveis por meio do [método EnumerateThreads](icordebugcontroller-enumeratethreads-method.md), de modo que os threads que foram suspensos com o método `SetAllThreadsDebugState` precisarão ser retomados com o método `SetAllThreadsDebugState`.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Veja também
