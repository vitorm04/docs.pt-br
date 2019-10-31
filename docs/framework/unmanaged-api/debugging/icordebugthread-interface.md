---
title: Interface ICorDebugThread
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
ms.openlocfilehash: c7333f4210d0a2ec4ff71a0fac0ea00068fecc57
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133506"
---
# <a name="icordebugthread-interface"></a>Interface ICorDebugThread
Representa um thread em um processo. O tempo de vida de uma instância `ICorDebugThread` é igual ao tempo de vida do thread que ela representa.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método ClearCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-clearcurrentexception-method.md)|Este método não está implementado. Não o use.|  
|[Método CreateEval](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-createeval-method.md)|Cria um objeto ICorDebugEval que opera neste `ICorDebugThread`.|  
|[Método CreateStepper](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-createstepper-method.md)|Cria um objeto ICorDebugStepper que permite percorrer o quadro ativo neste `ICorDebugThread`.|  
|[Método EnumerateChains](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-enumeratechains-method.md)|Obtém um ponteiro de interface para um enumerador ICorDebugChainEnum que contém todas as cadeias de pilha nesta `ICorDebugThread`.|  
|[Método GetActiveChain](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getactivechain-method.md)|Obtém um ponteiro de interface para o ICorDebugChain ativo neste `ICorDebugThread`.|  
|[Método GetActiveFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getactiveframe-method.md)|Obtém um ponteiro de interface para o ICorDebugFrame ativo neste `ICorDebugThread`.|  
|[Método GetAppDomain](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getappdomain-method.md)|Obtém um ponteiro de interface para o domínio do aplicativo no qual este `ICorDebugThread` está em execução no momento.|  
|[Método GetCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md)|Obtém um ponteiro de interface para um objeto ICorDebugValue que representa uma exceção que está sendo lançada atualmente pelo código gerenciado.|  
|[Método GetDebugState](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getdebugstate-method.md)|Obtém um valor de CorDebugThreadState que descreve o estado de depuração atual desta `ICorDebugThread`.|  
|[Método GetHandle](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-gethandle-method.md)|Obtém o identificador atual da parte ativa deste `ICorDebugThread`.|  
|[Método GetID](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getid-method.md)|Obtém o identificador do sistema operacional atual da parte ativa deste `ICorDebugThread`.|  
|[Método GetObject](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getobject-method.md)|Obtém um ponteiro de interface para o thread Common Language Runtime (CLR).|  
|[Método GetProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getprocess-method.md)|Obtém um ponteiro de interface para o processo do qual esse `ICorDebugThread` forma uma parte.|  
|[Método GetRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getregisterset-method.md)|Obtém um ponteiro de interface para o conjunto de registros associado a este `ICorDebugThread`.|  
|[Método GetUserState](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getuserstate-method.md)|Obtém uma combinação de bits de valor CorDebugUserState que descreve o estado atual desta `ICorDebugThread`.|  
|[Método SetDebugState](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md)|Define uma combinação de bits de `CorDebugThreadState` de valores que descreve o estado de depuração deste `ICorDebugThread`.|  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
> Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
