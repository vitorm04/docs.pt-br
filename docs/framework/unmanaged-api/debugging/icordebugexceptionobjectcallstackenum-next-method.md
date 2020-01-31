---
title: Método ICorDebugExceptionObjectCallStackEnum::Next
ms.date: 03/30/2017
api_name:
- ICorDebugExceptionObjectCallStackEnum::Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugExceptionObjectCallStackEnum::Next
helpviewer_keywords:
- ICorDebugExceptionObjectCallStackEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugExceptionObjectCallStackEnum interface [.NET Framework debugging]
ms.assetid: 3328a2c0-1e48-4a54-802a-9b474cf82c21
topic_type:
- apiref
ms.openlocfilehash: 38de810509f15cf93475eb000837892b99684fc9
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782747"
---
# <a name="icordebugexceptionobjectcallstackenumnext-method"></a>Método ICorDebugExceptionObjectCallStackEnum::Next
Obtém o número especificado de instâncias [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) que contêm informações de uma pilha de chamadas do objeto de exceção.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)] CorDebugExceptionObjectStackFrame values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `celt`  
 no O número de instâncias de [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) a serem recuperadas.  
  
 `values`  
 fora Uma matriz de ponteiros, cada um dos quais aponta para um objeto [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) .  
  
 `pceltFetched`  
 fora Um ponteiro para o número de instâncias de [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) retornadas na verdade.  
  
## <a name="remarks"></a>Comentários  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
