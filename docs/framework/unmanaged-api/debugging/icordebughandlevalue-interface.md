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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3219554cf953b8de31e236b2f484478172673f7b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915000"
---
# <a name="icordebughandlevalue-interface"></a>Interface ICorDebugHandleValue

Uma subclasse de ICorDebugReferenceValue que representa um valor de referência para o qual o depurador criou um identificador para a coleta de lixo.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método Dispose](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-dispose-method.md)|Libera o identificador referenciado por `ICorDebugHandleValue` este objeto sem liberar explicitamente o ponteiro de interface.|  
|[Método GetHandleType](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-gethandletype-method.md)|Obtém um valor CorDebugHandleType que descreve o tipo de identificador referenciado por `ICorDebugHandleValue`isso.|  
  
## <a name="remarks"></a>Comentários  
 Um `ICorDebugReferenceValue` objeto é invalidado por uma interrupção na execução de código depurado. Um `ICorDebugHandleValue` mantém sua referência por meio de interrupções e continuações até que seja liberado explicitamente.  
  
> [!NOTE]
> Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.  
  
## <a name="requirements"></a>Requisitos  
 **Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
