---
title: "Método ICorDebugMutableDataTarget::ContinueStatusChanged"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 5a66d3f4-dd16-4d62-9dcc-0eab7041d894
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2f4f3890f2cfb2e3b017b8c7d0705d8c8e063957
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmutabledatatargetcontinuestatuschanged-method"></a>Método ICorDebugMutableDataTarget::ContinueStatusChanged
Altera o status de continuação para o evento de depuração pendentes no thread especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT ContinueStatusChanged(  
   [in] DWORD dwThreadId,  
   [in] CORDB_CONTINUE_STATUS continueStatus);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwThreadId`  
 O identificador de thread definido pelo sistema operacional.  
  
 `continueStatus`  
 Um[COREDB_CONTINUE_STATUS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md)solicitado de valor que representa o novo status de continuação.  
  
## <a name="remarks"></a>Comentários  
 As chamadas do depurador de `ContinueStatusChanged` método quando ele chama um método ICorDebug que requer que o evento de depuração atual deve ser tratado de forma que é potencialmente diferente da maneira em que ele normalmente seria manipulado. Por exemplo, se há uma exceção pendente e o depurador solicita uma operação que cancelará a exceção (como [Icordebugilframe](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) ou `FuncEval`), essa API é usada para solicitar que a exceção seja cancelada.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorDebugMutableDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)  
 [Interfaces de depuração](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
