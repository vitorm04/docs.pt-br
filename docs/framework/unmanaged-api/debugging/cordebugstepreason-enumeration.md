---
title: Enumeração CorDebugStepReason
ms.date: 03/30/2017
api_name:
- CorDebugStepReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugStepReason
helpviewer_keywords:
- CorDebugStepReason enumeration [.NET Framework debugging]
ms.assetid: fe248069-b33c-48e1-a777-06ac9b239c54
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 71dcc34fd3489fc71cec4050b168548927833082
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="cordebugstepreason-enumeration"></a>Enumeração CorDebugStepReason
Indica o resultado de uma etapa individual.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef enum CorDebugStepReason {  
    STEP_NORMAL,  
    STEP_RETURN,  
    STEP_CALL,  
    STEP_EXCEPTION_FILTER,  
    STEP_EXCEPTION_HANDLER,  
    STEP_INTERCEPT,  
    STEP_EXIT  
} CorDebugStepReason;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`STEP_NORMAL`|Passo a passo concluída normalmente, dentro da mesma função.|  
|`STEP_RETURN`|Passo a passo continuação normalmente, depois que a função retornou.|  
|`STEP_CALL`|Passo a passo continuação normalmente, no início de uma função chamada recentemente.|  
|`STEP_EXCEPTION_FILTER`|Uma exceção foi gerada e o controle foi passado para um filtro de exceção.|  
|`STEP_EXCEPTION_HANDLER`|Uma exceção foi gerada e o controle foi passado para um manipulador de exceção.|  
|`STEP_INTERCEPT`|Controle foi passado para um interceptador.|  
|`STEP_EXIT`|O thread foi encerrado antes que a etapa foi concluída.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Método StepComplete](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md)  
 [Declarando enumerações](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
