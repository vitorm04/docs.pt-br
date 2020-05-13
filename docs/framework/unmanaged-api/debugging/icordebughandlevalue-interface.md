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
ms.openlocfilehash: c901e21521e941c51939958175a5316808890e9f
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83208610"
---
# <a name="icordebughandlevalue-interface"></a>Interface ICorDebugHandleValue

Uma subclasse de ICorDebugReferenceValue que representa um valor de referência para o qual o depurador criou um identificador para a coleta de lixo.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método Dispose](icordebughandlevalue-dispose-method.md)|Libera o identificador referenciado por este `ICorDebugHandleValue` objeto sem liberar explicitamente o ponteiro de interface.|  
|[Método GetHandleType](icordebughandlevalue-gethandletype-method.md)|Obtém um valor CorDebugHandleType que descreve o tipo de identificador referenciado por isso `ICorDebugHandleValue` .|  
  
## <a name="remarks"></a>Comentários  
 Um `ICorDebugReferenceValue` objeto é invalidado por uma interrupção na execução de código depurado. Um `ICorDebugHandleValue` mantém sua referência por meio de interrupções e continuações até que seja liberado explicitamente.  
  
> [!NOTE]
> Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Depurando interfaces](debugging-interfaces.md)
