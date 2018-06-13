---
title: ICorDebugThread Interface1
ms.date: 03/30/2017
api_name:
- ICorDebugThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread
helpviewer_keywords:
- ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 3930fd9b-2bc3-4b72-80a0-b6eeb94d60c6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 404f1bdf5865733648084e34a558b7b20a59b3ee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423072"
---
# <a name="icordebugthread-interface1"></a>ICorDebugThread Interface1
Representa um thread em um processo. O tempo de vida de uma instância `ICorDebugThread` é igual ao tempo de vida do thread que ela representa.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método ClearCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-clearcurrentexception-method.md)|Este método não está implementado. Não o use.|  
|[Método CreateEval](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-createeval-method.md)|Cria um objeto de ICorDebugEval que opera sobre isso `ICorDebugThread`.|  
|[Método CreateStepper](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-createstepper-method.md)|Cria um objeto de ICorDebugStepper que permite percorrer o quadro ativo na `ICorDebugThread`.|  
|[Método EnumerateChains](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-enumeratechains-method.md)|Obtém um ponteiro de interface para um enumerador de ICorDebugChainEnum que contém todas as cadeias de pilha neste `ICorDebugThread`.|  
|[Método GetActiveChain](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getactivechain-method.md)|Obtém um ponteiro de interface para o ativo ICorDebugChain neste `ICorDebugThread`.|  
|[Método GetActiveFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getactiveframe-method.md)|Obtém um ponteiro de interface para o ativo ICorDebugFrame neste `ICorDebugThread`.|  
|[Método GetAppDomain](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getappdomain-method.md)|Obtém um ponteiro de interface para o domínio de aplicativo no qual este `ICorDebugThread` está em execução atualmente.|  
|[Método GetCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md)|Obtém um ponteiro de interface para um objeto ICorDebugValue que representa uma exceção atualmente sendo lançada pelo código gerenciado.|  
|[Método GetDebugState](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getdebugstate-method.md)|Obtém um valor de CorDebugThreadState que descreve o estado atual de depuração deste `ICorDebugThread`.|  
|[Método GetHandle](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-gethandle-method.md)|Obtém o identificador atual para a parte ativa disso `ICorDebugThread`.|  
|[Método GetID](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getid-method.md)|Obtém o identificador de sistema operacional atual da parte ativa disso `ICorDebugThread`.|  
|[Método GetObject](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getobject-method.md)|Obtém um ponteiro de interface para o thread de runtime (CLR) de linguagem comum.|  
|[Método GetProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getprocess-method.md)|Obtém um ponteiro de interface para o processo do qual este `ICorDebugThread` faz parte.|  
|[Método GetRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getregisterset-method.md)|Obtém um ponteiro de interface para o conjunto de registro associado a esta `ICorDebugThread`.|  
|[Método GetUserState](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getuserstate-method.md)|Obtém uma combinação bit a bit dos valores de CorDebugUserState que descrevem o estado atual deste `ICorDebugThread`.|  
|[Método SetDebugState](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md)|Define uma combinação bit a bit de `CorDebugThreadState` valores que descrevem o estado de depuração deste `ICorDebugThread`.|  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
>  Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
