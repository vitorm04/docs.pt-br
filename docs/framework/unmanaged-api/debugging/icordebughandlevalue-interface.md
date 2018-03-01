---
title: ICorDebugHandleValue Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b8df7b46bf22fa1a3a8633cbad7ad1a6582b4860
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebughandlevalue-interface1"></a>ICorDebugHandleValue Interface1
Uma subclasse de ICorDebugReferenceValue que representa um valor de referência para o qual o depurador criou um identificador para a coleta de lixo.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método Dispose](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-dispose-method.md)|Libera o identificador referenciado por este `ICorDebugHandleValue` objeto sem liberar explicitamente o ponteiro de interface.|  
|[Método GetHandleType](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-gethandletype-method.md)|Obtém um valor de CorDebugHandleType que descreve o tipo de identificador referenciada por este `ICorDebugHandleValue`.|  
  
## <a name="remarks"></a>Comentários  
 Um `ICorDebugReferenceValue` objeto é invalidado por uma quebra na execução de código depurado. Um `ICorDebugHandleValue` mantém sua referência por meio de quebras e continuação, até que ele seja liberado explicitamente.  
  
> [!NOTE]
>  Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
