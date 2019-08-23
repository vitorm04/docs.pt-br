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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1517d686c50923f5599e33436e0ad6126e8be140
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923149"
---
# <a name="icordebugthread-interface"></a>Interface ICorDebugThread
Representa um thread em um processo. O tempo de vida de uma instância `ICorDebugThread` é igual ao tempo de vida do thread que ela representa.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método ClearCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-clearcurrentexception-method.md)|Este método não está implementado. Não o use.|  
|[Método CreateEval](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-createeval-method.md)|Cria um objeto ICorDebugEval que opera sobre isso `ICorDebugThread`.|  
|[Método CreateStepper](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-createstepper-method.md)|Cria um objeto ICorDebugStepper que permite percorrer o quadro ativo neste `ICorDebugThread`.|  
|[Método EnumerateChains](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-enumeratechains-method.md)|Obtém um ponteiro de interface para um enumerador ICorDebugChainEnum que contém todas as cadeias `ICorDebugThread`de pilha neste.|  
|[Método GetActiveChain](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getactivechain-method.md)|Obtém um ponteiro de interface para o ICorDebugChain ativo neste `ICorDebugThread`.|  
|[Método GetActiveFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getactiveframe-method.md)|Obtém um ponteiro de interface para o ICorDebugFrame ativo neste `ICorDebugThread`.|  
|[Método GetAppDomain](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getappdomain-method.md)|Obtém um ponteiro de interface para o domínio do aplicativo no `ICorDebugThread` qual está sendo executado no momento.|  
|[Método GetCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md)|Obtém um ponteiro de interface para um objeto ICorDebugValue que representa uma exceção que está sendo lançada atualmente pelo código gerenciado.|  
|[Método GetDebugState](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getdebugstate-method.md)|Obtém um valor de CorDebugThreadState que descreve o estado de `ICorDebugThread`depuração atual disso.|  
|[Método GetHandle](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-gethandle-method.md)|Obtém o identificador atual da parte ativa deste `ICorDebugThread`.|  
|[Método GetID](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getid-method.md)|Obtém o identificador do sistema operacional atual da parte `ICorDebugThread`ativa deste.|  
|[Método GetObject](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getobject-method.md)|Obtém um ponteiro de interface para o thread Common Language Runtime (CLR).|  
|[Método GetProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getprocess-method.md)|Obtém um ponteiro de interface para o processo do qual `ICorDebugThread` este forma uma parte.|  
|[Método GetRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getregisterset-method.md)|Obtém um ponteiro de interface para o conjunto de registros associado `ICorDebugThread`a isso.|  
|[Método GetUserState](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getuserstate-method.md)|Obtém uma combinação de bits de valor CorDebugUserState que descreve o estado `ICorDebugThread`atual disso.|  
|[Método SetDebugState](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md)|Define uma combinação de bits `CorDebugThreadState` de valores que descreve o estado `ICorDebugThread`de depuração disso.|  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
> Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.  
  
## <a name="requirements"></a>Requisitos  
 **Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
