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
ms.openlocfilehash: 9d98bccdfb83cec547b185693c28f25017d3225f
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782807"
---
# <a name="icordebugexceptionobjectcallstackenum-interface"></a>Interface ICorDebugExceptionObjectCallStackEnum
Fornece um enumerador para informações de pilha de chamadas que são inseridas em um objeto de exceção. Essa interface é uma subclasse da interface ICorDebugEnum.  
  
## <a name="methods"></a>{1&gt;Métodos&lt;1}  
  
|Método|Descrição|  
|------------|-----------------|  
|[ICorDebugExceptionObjectCallStackEnum::Next](icordebugexceptionobjectcallstackenum-next-method.md)|Obtém um número especificado de objetos [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) que contêm informações sobre uma pilha de chamadas do objeto de exceção.|  
  
## <a name="remarks"></a>Comentários  
 A interface `ICorDebugExceptionObjectCallStackEnum` implementa a interface ICorDebugEnum.  
  
 Uma instância de `ICorDebugExceptionObjectCallStackEnum` é populada com objetos [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) chamando o método [ICorDebugExceptionObjectValue:: EnumerateExceptionCallStack](icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md) . Os itens da pilha de chamadas na coleção podem ser enumerados chamando o método [ICorDebugExceptionObjectCallStackEnum:: Next](icordebugexceptionobjectcallstackenum-next-method.md)  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Depurando interfaces](debugging-interfaces.md)
- [Depuração](index.md)
