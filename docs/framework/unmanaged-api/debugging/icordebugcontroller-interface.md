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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e2a083f46f24d6f3f24c63dd2415b85f975cfa29
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912860"
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
 Se `ICorDebugController` o estiver controlando um processo, o escopo incluirá todos os threads do processo. Se `ICorDebugController` o estiver controlando um domínio de aplicativo, o escopo incluirá somente os threads desse domínio de aplicativo específico.  
  
> [!NOTE]
> Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.  
  
## <a name="requirements"></a>Requisitos  
 **Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
