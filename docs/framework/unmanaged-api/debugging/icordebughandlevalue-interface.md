---
title: Interface ICorDebugHandleValue
ms.date: 03/30/2017
api_name:
- ICorDebugHandleValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHandleValue
helpviewer_keywords:
- ICorDebugHandleValue interface [.NET Framework debugging]
ms.assetid: 66fcd2b8-ac66-414b-83a8-75a925e17772
topic_type:
- apiref
ms.openlocfilehash: 406468fc6e2b68e8c8e1dfbd0f0f18cce3f013ab
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794452"
---
# <a name="icordebughandlevalue-interface"></a>Interface ICorDebugHandleValue

Uma subclasse de ICorDebugReferenceValue que representa um valor de referência para o qual o depurador criou um identificador para a coleta de lixo.  
  
## <a name="methods"></a>{1&gt;Métodos&lt;1}  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método Dispose](icordebughandlevalue-dispose-method.md)|Libera o identificador referenciado por este objeto `ICorDebugHandleValue` sem liberar explicitamente o ponteiro de interface.|  
|[Método GetHandleType](icordebughandlevalue-gethandletype-method.md)|Obtém um valor CorDebugHandleType que descreve o tipo de identificador referenciado por este `ICorDebugHandleValue`.|  
  
## <a name="remarks"></a>Comentários  
 Um objeto `ICorDebugReferenceValue` é invalidado por uma interrupção na execução de código depurado. Uma `ICorDebugHandleValue` mantém sua referência por meio de interrupções e continuas até que seja liberada explicitamente.  
  
> [!NOTE]
> Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Depurando interfaces](debugging-interfaces.md)
