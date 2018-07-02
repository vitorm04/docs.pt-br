---
title: Método ICorDebugMutableDataTarget::ContinueStatusChanged
ms.date: 03/30/2017
ms.assetid: 5a66d3f4-dd16-4d62-9dcc-0eab7041d894
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3d2560aa484c6965047b2fdaf2c539b8ab675bc8
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36207697"
---
# <a name="icordebugmutabledatatargetcontinuestatuschanged-method"></a>Método ICorDebugMutableDataTarget::ContinueStatusChanged
Altera o status de continuação para o evento de depuração pendente no thread especificado.  
  
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
 Um valor [COREDB_CONTINUE_STATUS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) que representa o novo status de continuação solicitado.  
  
## <a name="remarks"></a>Comentários  
 O depurador chama o método `ContinueStatusChanged` quando ele chama um método ICorDebug que exige que o evento de depuração atual seja tratado de modo potencialmente diferente da maneira como ele normalmente seria tratado. Por exemplo, se houver uma exceção pendente e o depurador solicitar uma operação que cancelaria a exceção (como [ICorDebugILFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) ou `FuncEval`), essa API será usada para solicitar que a exceção seja cancelada.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorDebugMutableDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)  
 [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
