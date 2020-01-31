---
title: Método ICorDebugAppDomain4::GetObjectForCCW
ms.date: 03/30/2017
ms.assetid: 2cacdb85-e7b8-42e7-b310-c3e8c22e5d33
ms.openlocfilehash: 50f46394c809321f0bd256e4c8d75b76fc7c2c70
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784855"
---
# <a name="icordebugappdomain4getobjectforccw-method"></a>Método ICorDebugAppDomain4::GetObjectForCCW
Obtém um objeto gerenciado de um ponteiro de COM Callable Wrapper (CCW).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetObjectForCCW(  
   [in]CORDB_ADDRESS ccwPointer,   
   [out]ICorDebugValue **ppManagedObject  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `ccwPointer`  
 no Um ponteiro de COM Callable Wrapper (CCW).  
  
 `ppManagedObject`  
 fora Um ponteiro para o endereço de um objeto "ICorDebugValue" que representa o objeto gerenciado que corresponde ao ponteiro do CCW fornecido.  
  
## <a name="remarks"></a>Comentários  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorDebugAppDomain4](icordebugappdomain4-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
