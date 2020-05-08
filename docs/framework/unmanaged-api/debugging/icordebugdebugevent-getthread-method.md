---
title: Método ICorDebugDebugEvent::GetThread
ms.date: 03/30/2017
ms.assetid: 4f2e9a2c-8369-4a07-a881-ad5422626353
ms.openlocfilehash: acce18517c105739417fc734b49ff004ca9546dc
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976372"
---
# <a name="icordebugdebugeventgetthread-method"></a>Método ICorDebugDebugEvent::GetThread
Obtém o thread no qual o evento ocorreu.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetThread(  
        [out]ICorDebugThread **ppThread  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 ppThread  
 [out] Um ponteiro para o endereço de um objeto ICorDebugThread que representa o thread no qual o evento ocorreu.  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
> Esse método está disponível somente com .NET Native.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorDebugDebugEvent](icordebugdebugevent-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
