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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7306ee61d750ae256c93c049819a23d3d61f7297
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61782649"
---
# <a name="icordebugstackwalksetcontext-method"></a>Método ICorDebugStackWalk::SetContext
Define o [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) o contexto atual de objeto para um contexto válido para o thread.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT SetContext([in] CorDebugSetContextFlag flag,  
                   [in] ULONG32 contextSize,  
                   [in, size_is(contextSize)] BYTE context[]);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `flag`  
 [in] Um [CorDebugSetContextFlag](../../../../docs/framework/unmanaged-api/debugging/cordebugsetcontextflag-enumeration.md) sinalizador que indica se o contexto é do quadro ativo na pilha ou um contexto obtido pelo desenrolamento de pilha.  
  
 `contextSize`  
 [in] O tamanho alocado do `CONTEXT` buffer.  
  
 `context`  
 [in] O `CONTEXT` buffer.  
  
## <a name="return-value"></a>Valor de retorno  
 Esse método retorna os HRESULTs específicos a seguir, bem como o HRESULT erros que indicam falha do método.  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|O `ICorDebugStackWalk` contexto de objeto foi definido com êxito.|  
|E_FAIL|O `ICorDebugStackWalk` contexto de objeto não foi definido.|  
|E_INVALIDARG|O contexto é nulo.|  
|HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)|O buffer de contexto é muito pequeno.|  
  
## <a name="exceptions"></a>Exceções  
  
## <a name="remarks"></a>Comentários  
 Esse método não altera o contexto atual do thread.  
  
 Definir o contexto atual para um contexto inválido pode causar resultados imprevisíveis de movimentador de pilhas.  
  
 Você pode recuperar uma cópia bit a bit exata deste contexto imediatamente chamando o [icordebugstackwalk:: GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) método.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Depuração](../../../../docs/framework/unmanaged-api/debugging/index.md)
