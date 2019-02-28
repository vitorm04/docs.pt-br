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
ms.openlocfilehash: 9f2223230b18f175427bfbfeaa46bf1406d8c7e5
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56976350"
---
# <a name="icordebugthread-interface"></a>Interface ICorDebugThread
Representa um thread em um processo. O tempo de vida de uma instância `ICorDebugThread` é igual ao tempo de vida do thread que ela representa.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método ClearCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-clearcurrentexception-method.md)|Este método não está implementado. Não o use.|  
|[Método CreateEval](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-createeval-method.md)|Cria um objeto de ICorDebugEval que opera sobre isso `ICorDebugThread`.|  
|[Método CreateStepper](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-createstepper-method.md)|Cria um objeto de ICorDebugStepper que permite percorrer o quadro ativo neste `ICorDebugThread`.|  
|[Método EnumerateChains](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-enumeratechains-method.md)|Obtém um ponteiro de interface para um enumerador de ICorDebugChainEnum que contém todas as cadeias de pilha neste `ICorDebugThread`.|  
|[Método GetActiveChain](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getactivechain-method.md)|Obtém um ponteiro de interface para o Active Directory ICorDebugChain neste `ICorDebugThread`.|  
|[Método GetActiveFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getactiveframe-method.md)|Obtém um ponteiro de interface para o Active Directory ICorDebugFrame neste `ICorDebugThread`.|  
|[Método GetAppDomain](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getappdomain-method.md)|Obtém um ponteiro de interface para o domínio do aplicativo no qual este `ICorDebugThread` está em execução atualmente.|  
|[Método GetCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md)|Obtém um ponteiro de interface para um objeto de ICorDebugValue que representa uma exceção que está sendo atualmente gerada pelo código gerenciado.|  
|[Método GetDebugState](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getdebugstate-method.md)|Obtém um valor de CorDebugThreadState que descreve o estado atual de depuração deste `ICorDebugThread`.|  
|[Método GetHandle](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-gethandle-method.md)|Obtém o identificador atual para a parte ativa disso `ICorDebugThread`.|  
|[Método GetID](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getid-method.md)|Obtém o identificador de sistema operacional atual da parte ativa disso `ICorDebugThread`.|  
|[Método GetObject](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getobject-method.md)|Obtém um ponteiro de interface para o thread comum a language runtime (CLR).|  
|[Método GetProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getprocess-method.md)|Obtém um ponteiro de interface para o processo do qual este `ICorDebugThread` faz parte.|  
|[Método GetRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getregisterset-method.md)|Obtém um ponteiro de interface para o conjunto de registro associado a este `ICorDebugThread`.|  
|[Método GetUserState](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getuserstate-method.md)|Obtém uma combinação bit a bit de valores de CorDebugUserState que descrevem o estado atual deste `ICorDebugThread`.|  
|[Método SetDebugState](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md)|Define uma combinação bit a bit de `CorDebugThreadState` valores que descrevem o estado de depuração deste `ICorDebugThread`.|  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
>  Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
