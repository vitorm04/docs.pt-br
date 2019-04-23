---
title: Estrutura COR_ACTIVE_FUNCTION
ms.date: 03/30/2017
api_name:
- COR_ACTIVE_FUNCTION
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_ACTIVE_FUNCTION
helpviewer_keywords:
- COR_ACTIVE_FUNCTION structure [.NET Framework debugging]
ms.assetid: ed86185f-2152-459c-961f-10c06d62e83f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c0400da0cd29d642a1be42be7e2b22213ae54b94
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59121765"
---
# <a name="coractivefunction-structure"></a>Estrutura COR_ACTIVE_FUNCTION
Contém informações sobre as funções que estão atualmente ativas nos quadros de um thread. Essa estrutura é usada o [ICorDebugThread2::GetActiveFunctions](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getactivefunctions-method.md) método.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef struct  _COR_ACTIVE_FUNCTION {  
    ICorDebugAppDomain   *pAppDomain;  
    ICorDebugModule      *pModule;  
    ICorDebugFunction2   *pFunction;  
    ULONG32              ilOffset;  
    ULONG32              flags;  
} COR_ACTIVE_FUNCTION;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`pAppDomain`|Ponteiro para o proprietário do domínio de aplicativo do `ilOffset` campo.|  
|`pModule`|Ponteiro para o proprietário do módulo do `ilOffset` campo.|  
|`pFunction`|Ponteiro para o proprietário da função do `ilOffset` campo.|  
|`ilOffset`|O deslocamento do MSIL (linguagem intermediária) Microsoft do quadro.|  
|`flags`|Reservado para extensibilidade futura.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Estruturas de depuração](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [Depuração](../../../../docs/framework/unmanaged-api/debugging/index.md)
