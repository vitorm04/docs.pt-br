---
title: Interface ICorDebugExceptionObjectCallStackEnum
ms.date: 03/30/2017
api_name:
- ICorDebugExceptionObjectCallStackEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugExceptionObjectCallStackEnum
helpviewer_keywords:
- ICorDebugExceptionObjectCallStackEnum interface [.NET Framework debugging]
ms.assetid: 39dffa18-c71b-48c4-b11d-e814631ab1e9
topic_type:
- apiref
ms.openlocfilehash: e6dd951b0f432d455d95bb60f4c42df64d5bee24
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82975986"
---
# <a name="icordebugexceptionobjectcallstackenum-interface"></a>Interface ICorDebugExceptionObjectCallStackEnum
Fornece um enumerador para informações de pilha de chamadas que são inseridas em um objeto de exceção. Essa interface é uma subclasse da interface ICorDebugEnum.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[ICorDebugExceptionObjectCallStackEnum:: Next](icordebugexceptionobjectcallstackenum-next-method.md)|Obtém um número especificado de objetos [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) que contêm informações sobre uma pilha de chamadas do objeto de exceção.|  
  
## <a name="remarks"></a>Comentários  
 A `ICorDebugExceptionObjectCallStackEnum` interface implementa a interface ICorDebugEnum.  
  
 Uma `ICorDebugExceptionObjectCallStackEnum` instância é populada com objetos [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) chamando o método [ICorDebugExceptionObjectValue:: EnumerateExceptionCallStack](icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md) . Os itens da pilha de chamadas na coleção podem ser enumerados chamando o método [ICorDebugExceptionObjectCallStackEnum:: Next](icordebugexceptionobjectcallstackenum-next-method.md)  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Depurando interfaces](debugging-interfaces.md)
- [Depuração](index.md)
