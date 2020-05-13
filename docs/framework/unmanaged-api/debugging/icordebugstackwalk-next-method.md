---
title: Método ICorDebugStackWalk::Next
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.Next Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::Next
helpviewer_keywords:
- ICorDebugStackWalk::Next method [.NET Framework debugging]
- Next method, ICorDebugStackWalk interface [.NET Framework debugging]
ms.assetid: 189c36be-028c-4fba-a002-5edfb8fcd07f
topic_type:
- apiref
ms.openlocfilehash: b89e968e9b12943c8192af3b280f8bd321a02110
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378785"
---
# <a name="icordebugstackwalknext-method"></a>Método ICorDebugStackWalk::Next
Move o objeto [ICorDebugStackWalk](icordebugstackwalk-interface.md) para o próximo quadro.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT Next();  
```  
  
## <a name="return-value"></a>Valor retornado  
 Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|O tempo de execução rebobinado com êxito para o próximo quadro (consulte comentários).|  
|E_FAIL|O `ICorDebugStackWalk` objeto não pôde ser avançado.|  
|CORDBG_S_AT_END_OF_STACK|O fim da pilha foi atingido como resultado desse desenrolamento.|  
|CORDBG_E_PAST_END_OF_STACK|O ponteiro de quadro já está no final da pilha; Portanto, nenhum quadro adicional pode ser acessado.|  
  
## <a name="exceptions"></a>Exceções  
  
## <a name="remarks"></a>Comentários  
 O `Next` método avança o `ICorDebugStackWalk` objeto para o quadro de chamada somente se o tempo de execução puder desenrolar o quadro atual. Caso contrário, o objeto avança para o próximo quadro que o tempo de execução é capaz de desenrolar.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface ICorDebugStackWalk](icordebugstackwalk-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
- [Depuração](index.md)
