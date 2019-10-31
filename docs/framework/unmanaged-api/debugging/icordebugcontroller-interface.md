---
title: Interface ICorDebugController
ms.date: 03/30/2017
api_name:
- ICorDebugController
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController
helpviewer_keywords:
- ICorDebugController interface [.NET Framework debugging]
ms.assetid: dbb1c4dc-269a-459b-ab1d-6c70788782ce
topic_type:
- apiref
ms.openlocfilehash: 27f991c12ea7786d6146b5731848ca5ad3a37e21
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125364"
---
# <a name="icordebugcontroller-interface"></a>Interface ICorDebugController

Representa um escopo, um <xref:System.Diagnostics.Process> ou um <xref:System.AppDomain>, em que o contexto de execução de código pode ser controlado.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|`ICorDebugController::CanCommitChanges`|Esse método é obsoleto.|  
|`ICorDebugController::CommitChanges`|Esse método é obsoleto.|  
|[Método continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)|Retoma a execução de threads gerenciados após uma chamada para [ICorDebugController:: Stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md).|  
|[Método Detach](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-detach-method.md)|Desanexa o depurador do domínio do processo ou do aplicativo.|  
|[Método EnumerateThreads](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md)|Obtém um enumerador para os threads gerenciados ativos no processo.|  
|[Método HasQueuedCallbacks](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)|Obtém um valor que indica se qualquer retorno de chamada gerenciado está na fila no momento para o thread especificado.|  
|[Método IsRunning](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-isrunning-method.md)|Obtém um valor que indica se os threads no processo estão em execução livremente no momento.|  
|[Método SetAllThreadsDebugState](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md)|Define o estado de depuração de todos os threads gerenciados no processo.|  
|[Método Stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md)|Executa uma parada cooperativa em todos os threads que estão executando código gerenciado no processo.|  
|[Método Terminate](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-terminate-method.md)|Encerra o processo com o código de saída especificado.|  
  
## <a name="remarks"></a>Comentários  
 Se `ICorDebugController` estiver controlando um processo, o escopo incluirá todos os threads do processo. Se `ICorDebugController` estiver controlando um domínio de aplicativo, o escopo incluirá somente os threads desse domínio de aplicativo específico.  
  
> [!NOTE]
> Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
