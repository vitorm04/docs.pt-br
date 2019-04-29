---
title: Enumeração CorDebugIntercept
ms.date: 03/30/2017
api_name:
- CorDebugIntercept
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugIntercept
helpviewer_keywords:
- CorDebugIntercept enumeration [.NET Framework debugging]
ms.assetid: 3d5b642e-7ef2-428b-a5ae-509c35ed461a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0791a59e0325668960dcfc98816920db55bcfb87
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61651695"
---
# <a name="cordebugintercept-enumeration"></a>Enumeração CorDebugIntercept
Indica os tipos de código que podem ser interceptadas (isto é, entrados).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef enum CorDebugIntercept {  
    INTERCEPT_NONE                = 0x0,  
    INTERCEPT_CLASS_INIT          = 0x01,  
    INTERCEPT_EXCEPTION_FILTER    = 0x02,  
    INTERCEPT_SECURITY            = 0x04,  
    INTERCEPT_CONTEXT_POLICY      = 0x08,  
    INTERCEPT_INTERCEPTION        = 0x10,  
    INTERCEPT_ALL                 = 0xffff  
} CorDebugIntercept;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`INTERCEPT_NONE`|Nenhum código pode ser interceptado.|  
|`INTERCEPT_CLASS_INIT`|Um construtor pode ser interceptado.|  
|`INTERCEPT_EXCEPTION_FILTER`|Um filtro de exceção pode ser interceptado.|  
|`INTERCEPT_SECURITY`|Código que impõe a segurança pode ser interceptado.|  
|`INTERCEPT_CONTEXT_POLICY`|Uma política de contexto pode ser interceptada.|  
|`INTERCEPT_INTERCEPTION`|Não usado.|  
|`INTERCEPT_ALL`|Todos os códigos podem ser interceptados.|  
  
## <a name="remarks"></a>Comentários  
 Use o [ICorDebugStepper:: Setinterceptmask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setinterceptmask-method.md) método para estabelecer os tipos de código que podem ser interceptadas.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Declarando enumerações](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
