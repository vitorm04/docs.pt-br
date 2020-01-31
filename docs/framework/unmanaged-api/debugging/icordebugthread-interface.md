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
ms.openlocfilehash: b227b374021136e78f7f061d235eb18eca5b9515
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791483"
---
# <a name="icordebugthread-interface"></a>Interface ICorDebugThread
Representa um thread em um processo. O tempo de vida de uma instância `ICorDebugThread` é igual ao tempo de vida do thread que ela representa.  
  
## <a name="methods"></a>{1&gt;Métodos&lt;1}  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método ClearCurrentException](icordebugthread-clearcurrentexception-method.md)|Este método não está implementado. Não o use.|  
|[Método CreateEval](icordebugthread-createeval-method.md)|Cria um objeto ICorDebugEval que opera neste `ICorDebugThread`.|  
|[Método CreateStepper](icordebugthread-createstepper-method.md)|Cria um objeto ICorDebugStepper que permite percorrer o quadro ativo neste `ICorDebugThread`.|  
|[Método EnumerateChains](icordebugthread-enumeratechains-method.md)|Obtém um ponteiro de interface para um enumerador ICorDebugChainEnum que contém todas as cadeias de pilha nesta `ICorDebugThread`.|  
|[Método GetActiveChain](icordebugthread-getactivechain-method.md)|Obtém um ponteiro de interface para o ICorDebugChain ativo neste `ICorDebugThread`.|  
|[Método GetActiveFrame](icordebugthread-getactiveframe-method.md)|Obtém um ponteiro de interface para o ICorDebugFrame ativo neste `ICorDebugThread`.|  
|[Método GetAppDomain](icordebugthread-getappdomain-method.md)|Obtém um ponteiro de interface para o domínio do aplicativo no qual este `ICorDebugThread` está em execução no momento.|  
|[Método GetCurrentException](icordebugthread-getcurrentexception-method.md)|Obtém um ponteiro de interface para um objeto ICorDebugValue que representa uma exceção que está sendo lançada atualmente pelo código gerenciado.|  
|[Método GetDebugState](icordebugthread-getdebugstate-method.md)|Obtém um valor de CorDebugThreadState que descreve o estado de depuração atual desta `ICorDebugThread`.|  
|[Método GetHandle](icordebugthread-gethandle-method.md)|Obtém o identificador atual da parte ativa deste `ICorDebugThread`.|  
|[Método GetID](icordebugthread-getid-method.md)|Obtém o identificador do sistema operacional atual da parte ativa deste `ICorDebugThread`.|  
|[Método GetObject](icordebugthread-getobject-method.md)|Obtém um ponteiro de interface para o thread Common Language Runtime (CLR).|  
|[Método GetProcess](icordebugthread-getprocess-method.md)|Obtém um ponteiro de interface para o processo do qual esse `ICorDebugThread` forma uma parte.|  
|[Método GetRegisterSet](icordebugthread-getregisterset-method.md)|Obtém um ponteiro de interface para o conjunto de registros associado a este `ICorDebugThread`.|  
|[Método GetUserState](icordebugthread-getuserstate-method.md)|Obtém uma combinação de bits de valor CorDebugUserState que descreve o estado atual desta `ICorDebugThread`.|  
|[Método SetDebugState](icordebugthread-setdebugstate-method.md)|Define uma combinação de bits de `CorDebugThreadState` de valores que descreve o estado de depuração deste `ICorDebugThread`.|  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
> Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Depurando interfaces](debugging-interfaces.md)
