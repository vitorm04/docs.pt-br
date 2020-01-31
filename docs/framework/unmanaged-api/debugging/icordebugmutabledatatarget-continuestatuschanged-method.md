---
title: Método ICorDebugMutableDataTarget::ContinueStatusChanged
ms.date: 03/30/2017
ms.assetid: 5a66d3f4-dd16-4d62-9dcc-0eab7041d894
ms.openlocfilehash: c918bb60fba5bc1ec3f0f7c58b103d05a3c7ddfd
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792870"
---
# <a name="icordebugmutabledatatargetcontinuestatuschanged-method"></a>Método ICorDebugMutableDataTarget::ContinueStatusChanged
Altera o status de continuação para o evento de depuração pendente no thread especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT ContinueStatusChanged(  
   [in] DWORD dwThreadId,  
   [in] CORDB_CONTINUE_STATUS continueStatus);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `dwThreadId`  
 O identificador de thread definido pelo sistema operacional.  
  
 `continueStatus`  
 Um valor [COREDB_CONTINUE_STATUS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) que representa o novo status de continuação solicitado.  
  
## <a name="remarks"></a>Comentários  
 O depurador chama o método `ContinueStatusChanged` quando ele chama um método ICorDebug que exige que o evento de depuração atual seja tratado de modo potencialmente diferente da maneira como ele normalmente seria tratado. Por exemplo, se houver uma exceção pendente e o depurador solicitar uma operação que cancelaria a exceção (como [ICorDebugILFrame::SetIP](icordebugilframe-setip-method.md) ou `FuncEval`), essa API será usada para solicitar que a exceção seja cancelada.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorDebugMutableDataTarget](icordebugmutabledatatarget-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
