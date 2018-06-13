---
title: ICorDebugController Interface1
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
ms.openlocfilehash: 230488201b637c5a53f41dd4c3f204b37e8984fd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33411464"
---
# <a name="icordebugcontroller-interface1"></a>ICorDebugController Interface1
Representa um escopo, um <xref:System.Diagnostics.Process> ou um <xref:System.AppDomain>, em que o contexto de execução de código pode ser controlado.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|`ICorDebugController::CanCommitChanges`|Esse método é obsoleto.|  
|`ICorDebugController::CommitChanges`|Esse método é obsoleto.|  
|[Método continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)|Retoma a execução de threads gerenciados após uma chamada para [Icordebugcontroller](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md).|  
|[Método Detach](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-detach-method.md)|Desanexa o depurador do domínio de aplicativo ou processo.|  
|[Método EnumerateThreads](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md)|Obtém um enumerador para os threads gerenciados ativos no processo.|  
|[Método HasQueuedCallbacks](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)|Obtém um valor que indica se qualquer retornos de chamada gerenciados atualmente na fila para o segmento especificado.|  
|[Método IsRunning](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-isrunning-method.md)|Obtém um valor que indica se os threads do processo estão em execução no momento livremente.|  
|[Método SetAllThreadsDebugState](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md)|Define o estado de depuração de todos os threads gerenciados no processo.|  
|[Método Stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md)|Executa uma parada cooperativa em todos os threads que estão executando o código gerenciado no processo.|  
|[Método Terminate](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-terminate-method.md)|Encerra o processo com o código de saída especificado.|  
  
## <a name="remarks"></a>Comentários  
 Se `ICorDebugController` é controlar um processo, o escopo inclui todos os threads do processo. Se `ICorDebugController` está controlando a um domínio de aplicativo, o escopo inclui apenas os segmentos de domínio de aplicativo específico.  
  
> [!NOTE]
>  Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
