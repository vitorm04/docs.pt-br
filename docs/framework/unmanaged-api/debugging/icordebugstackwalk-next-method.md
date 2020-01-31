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
ms.openlocfilehash: b76d17337408653d130ee0cb8594e759bdade37c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791864"
---
# <a name="icordebugstackwalknext-method"></a>Método ICorDebugStackWalk::Next
Move o objeto [ICorDebugStackWalk](icordebugstackwalk-interface.md) para o próximo quadro.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT Next();  
```  
  
## <a name="return-value"></a>Valor de retorno  
 Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|O tempo de execução rebobinado com êxito para o próximo quadro (consulte comentários).|  
|{1&gt;E_FAIL&lt;1}|O objeto `ICorDebugStackWalk` não pôde ser avançado.|  
|CORDBG_S_AT_END_OF_STACK|O fim da pilha foi atingido como resultado desse desenrolamento.|  
|CORDBG_E_PAST_END_OF_STACK|O ponteiro de quadro já está no final da pilha; Portanto, nenhum quadro adicional pode ser acessado.|  
  
## <a name="exceptions"></a>Exceções  
  
## <a name="remarks"></a>Comentários  
 O método `Next` avança o objeto `ICorDebugStackWalk` para o quadro de chamada somente se o tempo de execução puder desenrolar o quadro atual. Caso contrário, o objeto avança para o próximo quadro que o tempo de execução é capaz de desenrolar.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorDebugStackWalk](icordebugstackwalk-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
- [Depuração](index.md)
