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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 724db50285532c20132fbfd5262df26227db6742
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61782662"
---
# <a name="icordebugstackwalknext-method"></a>Método ICorDebugStackWalk::Next
Move o [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) objeto para o próximo quadro.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT Next();  
```  
  
## <a name="return-value"></a>Valor de retorno  
 Esse método retorna os HRESULTs específicos a seguir, bem como o HRESULT erros que indicam falha do método.  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|O tempo de execução retornou com êxito para o próximo quadro (consulte comentários).|  
|E_FAIL|O `ICorDebugStackWalk` objeto não pôde ser avançado.|  
|CORDBG_S_AT_END_OF_STACK|O final da pilha foi atingido devido essa desenrolamento.|  
|CORDBG_E_PAST_END_OF_STACK|O ponteiro de quadro já está no final da pilha; Portanto, não há quadros adicionais podem ser acessados.|  
  
## <a name="exceptions"></a>Exceções  
  
## <a name="remarks"></a>Comentários  
 O `Next` avanços de método a `ICorDebugStackWalk` somente se o tempo de execução poderá desenrolar o quadro atual do objeto para o quadro de chamada. Caso contrário, o objeto avança para o próximo quadro que o tempo de execução é capaz de desenrolamento.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)
- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Depuração](../../../../docs/framework/unmanaged-api/debugging/index.md)
