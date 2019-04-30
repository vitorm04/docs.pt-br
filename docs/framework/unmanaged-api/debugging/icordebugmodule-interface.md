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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 257011562a9ea687ef70b842c6d47219283e158e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988009"
---
# <a name="icordebugmodule-interface"></a>Interface ICorDebugModule

Representa um módulo de runtime (CLR) de linguagem comum, que é um arquivo executável ou uma biblioteca de vínculo dinâmico (DLL).  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método CreateBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-createbreakpoint-method.md)|Não implementado.|  
|[Método EnableClassLoadCallbacks](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-enableclassloadcallbacks-method.md)|Determina se o [icordebugmanagedcallback:: loadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) e [icordebugmanagedcallback:: Unloadclass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) retornos de chamada são chamados para esse módulo.|  
|[Método EnableJITDebugging](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-enablejitdebugging-method.md)|Determina se o compilador just-in-time (JIT) preserva informações de depuração para métodos neste módulo.|  
|[Método GetAssembly](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getassembly-method.md)|Obtém o assembly que contém esse módulo.|  
|[Método GetBaseAddress](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getbaseaddress-method.md)|Obtém o endereço base do módulo.|  
|[Método GetClassFromToken](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getclassfromtoken-method.md)|Obtém o ICorDebugClass dos metadados.|  
|[Método GetEditAndContinueSnapshot](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-geteditandcontinuesnapshot-method.md)|Preterido.|  
|[Método GetFunctionFromRVA](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getfunctionfromrva-method.md)|Não implementado.|  
|[Método GetFunctionFromToken](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getfunctionfromtoken-method.md)|Obtém a função que é especificada pelo token de metadados.|  
|[Método GetGlobalVariableValue](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getglobalvariablevalue-method.md)|Obtém um objeto de valor para a variável global especificada.|  
|[Método GetMetaDataInterface](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getmetadatainterface-method.md)|Obtém um ponteiro de interface de metadados que pode ser usado para examinar os metadados para o módulo.|  
|[Método GetName](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getname-method.md)|Obtém o nome do arquivo do módulo.|  
|[Método GetProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getprocess-method.md)|Obtém o processo que contém esse módulo.|  
|[Método GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getsize-method.md)|Obtém o tamanho do módulo em bytes.|  
|[Método GetToken](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-gettoken-method.md)|Obtém o token para a entrada da tabela para esse módulo.|  
|[Método IsDynamic](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-isdynamic-method.md)|Indica se o módulo dinâmico.|  
|[Método IsInMemory](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-isinmemory-method.md)|Indica se este módulo existe apenas na memória.|  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
>  Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
