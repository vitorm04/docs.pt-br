---
title: Método ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode
ms.date: 03/30/2017
dev_langs:
- cpp
ms.assetid: b3af44ec-7d41-425b-aed9-0c4379e5cbe9
ms.openlocfilehash: 2c0da899b3f6f3c229c6f5e5b4cafe48fdc19742
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792164"
---
# <a name="icordebugprocess8enableexceptioncallbacksoutsideofmycode-method"></a>Método ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode
[Com suporte no .NET Framework 4,6 e versões posteriores]  
  
 Habilita ou desabilita determinados tipos de retornos de chamada de exceção [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) .  
  
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
 Se o valor de `enableExceptionsOutsideOfJMC` for `false`:  
  
- Uma exceção DEBUG_EXCEPTION_FIRST_CHANCE não resultará em um retorno de chamada para o depurador.  
  
- Uma exceção de DEBUG_EXCEPTION_CATCH_HANDLER_FOUND não resultará em um retorno de chamada para o depurador se a exceção nunca sair do código do usuário (ou seja, o caminho de uma origem de exceção para um manipulador de exceção não tem nenhum método marcado como JustMyCode ou JMC).  
  
 O valor padrão de `enableExceptionsOutsideOfJMC` é `true`.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorDebugProcess8](icordebugprocess8-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
