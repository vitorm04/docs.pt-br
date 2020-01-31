---
title: Interface ICorDebugModule
ms.date: 03/30/2017
api_name:
- ICorDebugModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule
helpviewer_keywords:
- ICorDebugModule interface [.NET Framework debugging]
ms.assetid: 32e4d6fa-e5a3-413e-9166-d5e2871d3114
topic_type:
- apiref
ms.openlocfilehash: c573e6b768aee1e8b681dcf2e828dc24d409025b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793008"
---
# <a name="icordebugmodule-interface"></a>Interface ICorDebugModule

Representa um módulo Common Language Runtime (CLR), que é um arquivo executável ou uma DLL (biblioteca de vínculo dinâmico).  
  
## <a name="methods"></a>{1&gt;Métodos&lt;1}  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método CreateBreakpoint](icordebugmodule-createbreakpoint-method.md)|Não implementado.|  
|[Método EnableClassLoadCallbacks](icordebugmodule-enableclassloadcallbacks-method.md)|Determina se os retornos de chamada [ICorDebugManagedCallback:: LoadClass](icordebugmanagedcallback-loadclass-method.md) e [ICorDebugManagedCallback:: UnloadClass](icordebugmanagedcallback-unloadclass-method.md) são chamados para este módulo.|  
|[Método EnableJITDebugging](icordebugmodule-enablejitdebugging-method.md)|Determina se o compilador JIT (just-in-time) preserva informações de depuração para métodos dentro deste módulo.|  
|[Método GetAssembly](icordebugmodule-getassembly-method.md)|Obtém o assembly recipiente para este módulo.|  
|[Método GetBaseAddress](icordebugmodule-getbaseaddress-method.md)|Obtém o endereço base do módulo.|  
|[Método GetClassFromToken](icordebugmodule-getclassfromtoken-method.md)|Obtém o ICorDebugClass dos metadados.|  
|[Método GetEditAndContinueSnapshot](icordebugmodule-geteditandcontinuesnapshot-method.md)|Preterido.|  
|[Método GetFunctionFromRVA](icordebugmodule-getfunctionfromrva-method.md)|Não implementado.|  
|[Método GetFunctionFromToken](icordebugmodule-getfunctionfromtoken-method.md)|Obtém a função que é especificada pelo token de metadados.|  
|[Método GetGlobalVariableValue](icordebugmodule-getglobalvariablevalue-method.md)|Obtém um objeto de valor para a variável global especificada.|  
|[Método GetMetaDataInterface](icordebugmodule-getmetadatainterface-method.md)|Obtém um ponteiro de interface de metadados que pode ser usado para examinar os metadados do módulo.|  
|[Método GetName](icordebugmodule-getname-method.md)|Obtém o nome do arquivo do módulo.|  
|[Método GetProcess](icordebugmodule-getprocess-method.md)|Obtém o processo de contenção deste módulo.|  
|[Método GetSize](icordebugmodule-getsize-method.md)|Obtém o tamanho do módulo em bytes.|  
|[Método GetToken](icordebugmodule-gettoken-method.md)|Obtém o token para a entrada de tabela deste módulo.|  
|[Método IsDynamic](icordebugmodule-isdynamic-method.md)|Indica se o módulo é dinâmico.|  
|[Método IsInMemory](icordebugmodule-isinmemory-method.md)|Indica se este módulo existe apenas na memória.|  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
> Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorDebug](icordebug-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
