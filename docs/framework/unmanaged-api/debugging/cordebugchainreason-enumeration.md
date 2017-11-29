---
title: "Enumeração CorDebugChainReason"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugChainReason
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugChainReason
helpviewer_keywords: CorDebugChainReason enumeration [.NET Framework debugging]
ms.assetid: c915da51-50b2-41df-841a-2b971f4d0975
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0d501db111256861a3d0a602712e4c32f40b7b6e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="cordebugchainreason-enumeration"></a>Enumeração CorDebugChainReason
Indica o motivo ou os motivos para o início de uma cadeia de chamadas.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef enum CorDebugChainReason {  
    CHAIN_NONE              = 0x000,  
    CHAIN_CLASS_INIT        = 0x001,  
    CHAIN_EXCEPTION_FILTER  = 0x002,  
    CHAIN_SECURITY          = 0x004,  
    CHAIN_CONTEXT_POLICY    = 0x008,  
    CHAIN_INTERCEPTION      = 0x010,  
    CHAIN_PROCESS_START     = 0x020,  
    CHAIN_THREAD_START      = 0x040,  
    CHAIN_ENTER_MANAGED     = 0x080,  
    CHAIN_ENTER_UNMANAGED   = 0x100,  
    CHAIN_DEBUGGER_EVAL     = 0x200,  
    CHAIN_CONTEXT_SWITCH    = 0x400,  
    CHAIN_FUNC_EVAL         = 0x800  
} CorDebugChainReason;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`CHAIN_NONE`|Nenhuma cadeia de chamada foi iniciada.|  
|`CHAIN_CLASS_INIT`|A cadeia foi iniciada por um construtor.|  
|`CHAIN_EXCEPTION_FILTER`|A cadeia foi iniciada por um filtro de exceção.|  
|`CHAIN_SECURITY`|A cadeia foi iniciada pelo código que impõe a segurança.|  
|`CHAIN_CONTEXT_POLICY`|A cadeia foi iniciada por uma política de contexto.|  
|`CHAIN_INTERCEPTION`|Não usado.|  
|`CHAIN_PROCESS_START`|Não usado.|  
|`CHAIN_THREAD_START`|A cadeia foi iniciada no início de uma execução de thread.|  
|`CHAIN_ENTER_MANAGED`|A cadeia foi iniciada por entrada no código gerenciado.|  
|`CHAIN_ENTER_UNMANAGED`|A cadeia foi iniciada com a entrada de código não gerenciado.|  
|`CHAIN_DEBUGGER_EVAL`|Não usado.|  
|`CHAIN_CONTEXT_SWITCH`|Não usado.|  
|`CHAIN_FUNC_EVAL`|A cadeia foi iniciada por uma avaliação de função.|  
  
## <a name="remarks"></a>Comentários  
 Use o [: Getreason](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md) método para determinar as razões para o início de uma cadeia de chamada.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Declarando enumerações](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
