---
title: Método ICorDebugExceptionObjectValue::EnumerateExceptionCallStack
ms.date: 03/30/2017
api_name:
- ICorDebugExceptionObjectValue.EnumerateExceptionCallStack
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugExceptionObjectValue::EnumerateExceptionCallStack
helpviewer_keywords:
- EnumerateExceptionCallStack method, ICorDebugExceptionObjectValue interface [.NET Framework debugging]
- ICorDebugExceptionObjectValue::EnumerateExceptionCallStack method [.NET Framework debugging]
ms.assetid: 00c64533-15dd-47f4-bb97-fe80a1ebadef
topic_type:
- apiref
ms.openlocfilehash: 57eb284bfe39ce92b2d6c03a2aeb4ae84d6aba91
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788674"
---
# <a name="icordebugexceptionobjectvalueenumerateexceptioncallstack-method"></a>Método ICorDebugExceptionObjectValue::EnumerateExceptionCallStack
Obtém um enumerador para a pilha de chamadas inserido em um objeto de exceção.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT EnumerateExceptionCallStack(  
    [out] ICorDebugExceptionObjectCallStackEnum **ppCallStackEnum  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 ppCallStackEnum  
 fora Um ponteiro para o endereço de um objeto de interface [ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md) que é um enumerador de rastreamento de pilha para um objeto de exceção gerenciado.  
  
## <a name="remarks"></a>Comentários  
 Se nenhuma informação da pilha de chamadas estiver disponível, o método retornará `S_OK`e [ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md) será um enumerador válido com um comprimento de 0. Se o método não puder recuperar informações de rastreamento de pilha, o valor de retorno será `E_FAIL` e nenhum enumerador será retornado.  
  
 O objeto [ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md) é responsável por decodificar os dados de rastreamento de pilha do campo `_stackTrace` do objeto de exceção.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorDebugExceptionObjectValue](icordebugexceptionobjectvalue-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
