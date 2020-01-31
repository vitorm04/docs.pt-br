---
title: 'Método ICorDebugExceptionDebugEvent:: GetStackPointer'
ms.date: 03/30/2017
ms.assetid: d8f66a1c-16be-4264-afc5-bc2dfbb4a682
ms.openlocfilehash: 657649b97262a12639117defe7a9c546f08cfef5
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782848"
---
# <a name="icordebugexceptiondebugeventgetstackpointer-method"></a>Método ICorDebugExceptionDebugEvent:: GetStackPointer
Obtém o ponteiro de pilha para este evento de depuração de exceção.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetStackPointer(  
   [out]CORDB_ADDRESS *pStackPointer  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pStackPointer`  
 fora Um ponteiro para o endereço do ponteiro de pilha para este evento de depuração de exceção. Consulte a seção Comentários para obter mais informações.  
  
## <a name="remarks"></a>Comentários  
 O significado desse ponteiro de pilha depende do tipo de evento, conforme mostrado na tabela a seguir.  
  
|Tipo de evento|Significado do valor de `pStackPointer`|  
|----------------|--------------------------------------|  
|[MANAGED_EXCEPTION_FIRST_CHANCE](cordebugrecordformat-enumeration.md)|O ponteiro de pilha para o quadro que gerou a exceção.|  
|[MANAGED_EXCEPTION_USER_FIRST_CHANCE](cordebugrecordformat-enumeration.md)|O ponteiro de pilha para o quadro de código do usuário mais próximo do ponto da exceção gerada.|  
|[MANAGED_EXCEPTION_CATCH_HANDLER_FOUND](cordebugrecordformat-enumeration.md)|O ponteiro de pilha para o quadro que contém o manipulador catch.|  
|[MANAGED_EXCEPTION_UNHANDLED](cordebugrecordformat-enumeration.md)|`pStackPointer` é **nulo**.|  
  
> [!NOTE]
> Esse método está disponível somente com .NET Native.  
  
 O tipo de evento está disponível no método [ICorDebugDebugEvent:: GetEventKind](icordebugdebugevent-geteventkind-method.md) .  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorDebugExceptionDebugEvent](icordebugexceptiondebugevent-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
