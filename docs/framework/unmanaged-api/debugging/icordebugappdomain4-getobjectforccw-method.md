---
title: Método ICorDebugAppDomain4::GetObjectForCCW
ms.date: 03/30/2017
ms.assetid: 2cacdb85-e7b8-42e7-b310-c3e8c22e5d33
ms.openlocfilehash: 10d32314e46aba4f030b294cadc3cbb36e8742f8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179045"
---
# <a name="icordebugappdomain4getobjectforccw-method"></a>Método ICorDebugAppDomain4::GetObjectForCCW
Obtém um objeto gerenciado a partir de um ponteiro de invólucro callable (CCW) COM.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetObjectForCCW(  
   [in]CORDB_ADDRESS ccwPointer,
   [out]ICorDebugValue **ppManagedObject  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `ccwPointer`  
 [em] Um ponteiro de invólucro callable COM (CCW).  
  
 `ppManagedObject`  
 [fora] Um ponteiro para o endereço de um objeto "ICorDebugValue" que representa o objeto gerenciado que corresponde ao ponteiro CCW dado.  
  
## <a name="remarks"></a>Comentários  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface ICorDebugAppDomain4](icordebugappdomain4-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
