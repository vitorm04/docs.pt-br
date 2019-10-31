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
ms.openlocfilehash: cbc272070e9eb6810b34ec1f3fdc9e944c624cd3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132376"
---
# <a name="cor_active_function-structure"></a>Estrutura COR_ACTIVE_FUNCTION
Contém informações sobre as funções que estão atualmente ativas nos quadros de um thread. Essa estrutura é usada pelo método [ICorDebugThread2:: GetActiveFunctions](icordebugthread2-getactivefunctions-method.md) .  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
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
|`pAppDomain`|Ponteiro para o proprietário do domínio de aplicativo do campo `ilOffset`.|  
|`pModule`|Ponteiro para o proprietário do módulo do campo `ilOffset`.|  
|`pFunction`|Ponteiro para o proprietário da função do campo `ilOffset`.|  
|`ilOffset`|O deslocamento da MSIL (Microsoft Intermediate Language) do quadro.|  
|`flags`|Reservado para extensibilidade futura.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug. idl  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Estruturas de depuração](debugging-structures.md)
- [Depuração](index.md)
