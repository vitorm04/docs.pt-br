---
title: Interface ICorDebugProcess2
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2
helpviewer_keywords:
- ICorDebugProcess2 interface [.NET Framework debugging]
ms.assetid: 73332138-5fea-441f-b893-61af87d45a42
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c3009ee6a2ba22771a2132032744f76ca527c422
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965677"
---
# <a name="icordebugprocess2-interface"></a>Interface ICorDebugProcess2
Uma extensão lógica da interface ICorDebugProcess, que representa um processo em execução de código gerenciado.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método ClearUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-clearunmanagedbreakpoint-method.md)|Remove um ponto de interrupção no deslocamento especificado que foi definido por uma chamada anterior para `ICorDebugProcess2::SetUnmanagedBreakpoint`.|  
|[Método GetDesiredNGENCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getdesiredngencompilerflags-method.md)|Obtém os sinalizadores que devem ser definidos para o common language runtime (CLR) para carregar a imagem no processo referenciado por este `ICorDebugProcess2`.|  
|[Método GetReferenceValueFromGCHandle](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getreferencevaluefromgchandle-method.md)|Obtém um ponteiro de referência para o objeto especificado gerenciado que possua uma coleta de lixo a alça.|  
|[Método GetThreadForTaskID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getthreadfortaskid-method.md)|Obtém o thread no qual a tarefa com o identificador especificado está em execução.|  
|[Método GetVersion](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getversion-method.md)|Obtém a versão do CLR na qual o processo que está sendo depurado está em execução.|  
|[Método SetDesiredNGENCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setdesiredngencompilerflags-method.md)|Define os sinalizadores que são necessários para o compilador just-in-time (JIT) carregar uma imagem no processo sendo depurado.|  
|[Método SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md)|Define um ponto de interrupção não gerenciado no deslocamento especificado de imagem nativa.|  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
>  Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
