---
title: Método ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode
ms.date: 03/30/2017
dev_langs:
- cpp
ms.assetid: b3af44ec-7d41-425b-aed9-0c4379e5cbe9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 08937e87b8bd2249b8608f8ec1ed1f7734961b3b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61948558"
---
# <a name="icordebugprocess8enableexceptioncallbacksoutsideofmycode-method"></a>Método ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode
[Com suporte no [!INCLUDE[net_v46](../../../../includes/net-v46-md.md)] e versões posteriores]  
  
 Habilita ou desabilita determinados tipos de [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) retornos de chamada de exceção.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT EnableExceptionCallbacksOutsideOfMyCode(  
   [in] BOOL enableExceptionsOutsideOfJMC  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `enableExceptionsOutsideOfJMC`  
 [in]  
  
## <a name="remarks"></a>Comentários  
 Se o valor de `enableExceptionsOutsideOfJMC` é `false`:  
  
- Uma exceção DEBUG_EXCEPTION_FIRST_CHANCE não resultará em um retorno de chamada para o depurador.  
  
- Uma exceção DEBUG_EXCEPTION_CATCH_HANDLER_FOUND não resultará em um retorno de chamada para o depurador se a exceção escapa nunca no código do usuário (ou seja, o caminho de uma origem da exceção para um manipulador de exceção não tem métodos marcados como JustMyCode ou JMC).  
  
 O valor padrão de `enableExceptionsOutsideOfJMC` é `true`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorDebugProcess8](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess8-interface.md)
- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
