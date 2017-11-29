---
title: Interface ICorDebugStackWalk
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStackWalk
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStackWalk
helpviewer_keywords: ICorDebugStackWalk interface [.NET Framework debugging]
ms.assetid: 16d695e8-975d-431b-8421-e9e6c3e3f476
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0c8a4421b716614081368755388bd2ab8d8fe22e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugstackwalk-interface"></a>Interface ICorDebugStackWalk
Fornece métodos para colocar os métodos gerenciados, ou quadros, em uma pilha de thread.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md)|Retorna o contexto para o quadro atual de `ICorDebugStackWalk` objeto.|  
|[Método SetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-setcontext-method.md)|Define o `ICorDebugStackWalk` o contexto atual do objeto para um contexto válido para o thread.|  
|[Próximo método](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-next-method.md)|Move o `ICorDebugStackWalk` objeto para o próximo quadro.|  
|[Método GetFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getframe-method.md)|Obtém o quadro atual de `ICorDebugStackWalk` objeto.|  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
>  Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de depuração](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Depuração](../../../../docs/framework/unmanaged-api/debugging/index.md)
