---
title: Método ICorDebugThread::SetDebugState
ms.date: 03/30/2017
api_name:
- ICorDebugThread.SetDebugState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::SetDebugState
helpviewer_keywords:
- ICorDebugThread::SetDebugState method [.NET Framework debugging]
- SetDebugState method [.NET Framework debugging]
ms.assetid: 6382bdf6-d488-4952-b653-cb09b6e1c6c2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d29f5cefd22592fa8949ff5361109c09c0972b24
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57499687"
---
# <a name="icordebugthreadsetdebugstate-method"></a>Método ICorDebugThread::SetDebugState
Define os sinalizadores que descrevem o estado de depuração deste ICorDebugThread.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT SetDebugState (  
    [in] CorDebugThreadState state  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `state`  
 [in] Uma combinação bit a bit dos valores de enumeração CorDebugThreadState que especificam o estado de depuração desse thread.  
  
## <a name="remarks"></a>Comentários  
 `SetDebugState` Define o estado de depuração atual do thread. (O "estado atual de depuração" representa o estado de depuração se o processo de ser continuada, não o estado atual propriamente dito.) O valor normal é THREAD_RUNNING. Somente o depurador pode afetar o estado de depuração de um thread. Estados de depuração pela última vez em continuar, portanto, se você quiser manter um thread continua THREAD_SUSPENDed ao longo de vários, você pode defini-lo uma vez e depois disso não precisa se preocupar sobre ele. Suspendendo threads e reiniciando o processo podem causar deadlocks, embora seja improvável normalmente. Essa é uma qualidade intrínseco de threads e processos e é por design. Um depurador assincronamente pode interromper e retomar os threads para quebrar o deadlock. Se o estado do usuário do thread inclui USER_UNSAFE_POINT, o thread pode bloquear uma coleta de lixo (GC). Isso significa que o thread suspenso tem uma chance maior de causar um deadlock. Isso pode não afetar a depuração de eventos já na fila. Assim, um depurador deve drenar a fila de evento completa (chamando [icordebugcontroller:: Hasqueuedcallbacks](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)) antes de suspender ou retomar os threads. Caso contrário ele poderá receber eventos em um thread que ele acredita que ele suspendeu.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
