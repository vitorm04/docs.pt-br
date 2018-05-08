---
title: Enumeração CorDebugInternalFrameType
ms.date: 03/30/2017
api_name:
- CorDebugInternalFrameType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugInternalFrameType
helpviewer_keywords:
- CorDebugInternalFrameType enumeration [.NET Framework debugging]
ms.assetid: e4412dc2-c338-4cfb-94d8-f682095dd2b1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 49b42a7fc54af56149b602b337e4a6c853c270cd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="cordebuginternalframetype-enumeration"></a>Enumeração CorDebugInternalFrameType
Identifica o tipo de quadro de pilha. Essa enumeração é usada pelo [Icordebuginternalframe](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-getframetype-method.md) método.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef enum CorDebugInternalFrameType {  
  
    STUBFRAME_NONE                 = 0x00000000,  
    STUBFRAME_M2U                  = 0x00000001,  
    STUBFRAME_U2M                  = 0x00000002,  
    STUBFRAME_APPDOMAIN_TRANSITION = 0x00000003,  
    STUBFRAME_LIGHTWEIGHT_FUNCTION = 0x00000004,  
    STUBFRAME_FUNC_EVAL            = 0x00000005,  
    STUBFRAME_INTERNALCALL         = 0x00000006,  
    STUBFRAME_CLASS_INIT           = 0x00000007,  
    STUBFRAME_EXCEPTION            = 0x00000008,  
    STUBFRAME_SECURITY             = 0x00000009,  
    STUBFRAME_JIT_COMPILATION     = 0x0000000a,  
} CorDebugInternalFrameType;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`STUBFRAME_NONE`|Um valor nulo. O `ICorDebugInternalFrame::GetFrameType` método nunca retorna esse valor.|  
|`STUBFRAME_M2U`|Um quadro de stub para gerenciado.|  
|`STUBFRAME_U2M`|Um quadro de stub não gerenciado para gerenciado.|  
|`STUBFRAME_APPDOMAIN_TRANSITION`|Uma transição entre domínios de aplicativo.|  
|`STUBFRAME_LIGHTWEIGHT_FUNCTION`|Uma chamada de método leve.|  
|`STUBFRAME_FUNC_EVAL`|O início da avaliação de função.|  
|`STUBFRAME_INTERNALCALL`|Uma chamada interna no common language runtime.|  
|`STUBFRAME_CLASS_INIT`|O início de uma classe de inicialização.|  
|`STUBFRAME_EXCEPTION`|Uma exceção que é lançada.|  
|`STUBFRAME_SECURITY`|Um quadro usado para a segurança de acesso do código.|  
|`STUBFRAME_JIT_COMPILATION`|O tempo de execução é um método de compilação JIT.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Declarando enumerações](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
