---
title: Interface ICorDebugValue3
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
- ICorDebugValue3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue3
helpviewer_keywords:
- ICorDebugValue3 interface [.NET Framework debugging]
ms.assetid: 7d5385d3-f4a5-47c4-8478-a3513b5e9406
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6a470113dc54876937850294f6d99fc15a2cf98e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvalue3-interface"></a>Interface ICorDebugValue3
Estende as interfaces "ICorDebugValue" e "ICorDebugValue2" para oferecer suporte para matrizes que são maiores do que 2 GB.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método GetSize64](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md)|Obtém o tamanho, em bytes, isso `ICorDebugValue3` objeto.|  
  
## <a name="remarks"></a>Comentários  
 O [Icordebugvalue](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md) método retorna um tamanho de objeto que varia de 0 a 2.147.483.647 bytes. No [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], o tamanho das matrizes pode exceder 2 GB. O `ICorDebugValue3` interface permite que você determine o tamanho desses conjuntos.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
    
    
 [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Depuração](../../../../docs/framework/unmanaged-api/debugging/index.md)
