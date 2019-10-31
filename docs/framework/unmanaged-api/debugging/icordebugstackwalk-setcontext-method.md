---
title: Método ICorDebugStackWalk::SetContext
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.SetContext Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::SetContext
helpviewer_keywords:
- SetContext method [.NET Framework debugging]
- ICorDebugStackWalk::SetContext method [.NET Framework debugging]
ms.assetid: bac0b156-31a3-4e7f-be4d-ab21789c81f1
topic_type:
- apiref
ms.openlocfilehash: 90156152a2c133446dedbe22426785ab63f8dfb9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131808"
---
# <a name="icordebugstackwalksetcontext-method"></a>Método ICorDebugStackWalk::SetContext
Define o contexto atual do objeto [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) como um contexto válido para o thread.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetContext([in] CorDebugSetContextFlag flag,  
                   [in] ULONG32 contextSize,  
                   [in, size_is(contextSize)] BYTE context[]);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `flag`  
 no Um sinalizador [CorDebugSetContextFlag](../../../../docs/framework/unmanaged-api/debugging/cordebugsetcontextflag-enumeration.md) que indica se o contexto é do quadro ativo na pilha ou um contexto obtido com o desenrolamento da pilha.  
  
 `contextSize`  
 no O tamanho alocado do buffer de `CONTEXT`.  
  
 `context`  
 no O buffer de `CONTEXT`.  
  
## <a name="return-value"></a>Valor retornado  
 Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|O contexto do objeto de `ICorDebugStackWalk` foi definido com êxito.|  
|E_FAIL|O contexto do objeto de `ICorDebugStackWalk` não foi definido.|  
|E_INVALIDARG|O contexto é nulo.|  
|HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)|O buffer de contexto é muito pequeno.|  
  
## <a name="exceptions"></a>Exceções  
  
## <a name="remarks"></a>Comentários  
 Esse método não altera o contexto atual do thread.  
  
 A definição do contexto atual como um contexto inválido pode causar resultados imprevisíveis do Stack Walker.  
  
 Você pode recuperar uma cópia de bit exata desse contexto chamando imediatamente o método [ICorDebugStackWalk:: GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) .  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Depuração](../../../../docs/framework/unmanaged-api/debugging/index.md)
