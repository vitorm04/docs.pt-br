---
title: Método ICorDebugProcess6::ProcessStateChanged
ms.date: 03/30/2017
ms.assetid: fb6d30d9-54f3-462b-8ebf-ce0440791ad5
ms.openlocfilehash: b6665df550a2d07a3fa84c3f2b6bf07f459cd713
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792212"
---
# <a name="icordebugprocess6processstatechanged-method"></a>Método ICorDebugProcess6::ProcessStateChanged
Notifica o [ICorDebug](icordebug-interface.md) de que o processo está em execução.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT ProcessStateChanged(   [in] CorDebugStateChange change);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `change`  
 no Um membro da enumeração [ProcessStateChanged](icordebugprocess6-processstatechanged-method.md)  
  
## <a name="remarks"></a>Comentários  
 O depurador chama esse método para notificar [ICorDebug](icordebug-interface.md) que o processo está em execução.  
  
> [!NOTE]
> Esse método está disponível somente com .NET Native.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorDebugProcess6](icordebugprocess6-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
