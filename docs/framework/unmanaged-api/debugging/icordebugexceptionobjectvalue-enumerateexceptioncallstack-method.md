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
ms.openlocfilehash: e45b180ac6d943d89740ad7ae10500ea4ad1aa9c
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82975960"
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
 Se nenhuma informação da pilha de chamadas estiver disponível, o `S_OK`método retornará e [ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md) será um enumerador válido com um comprimento de 0. Se o método não puder recuperar informações de rastreamento de pilha, o valor de `E_FAIL` retorno será e nenhum enumerador será retornado.  
  
 O objeto [ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md) é responsável por decodificar os dados de rastreamento de pilha `_stackTrace` do campo do objeto de exceção.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorDebugExceptionObjectValue](icordebugexceptionobjectvalue-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
