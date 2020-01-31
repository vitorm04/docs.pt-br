---
title: Interface ICorDebugVirtualUnwinder
ms.date: 03/30/2017
ms.assetid: a09e9ccc-0b37-43e3-95c1-bc5fa7ee5f42
ms.openlocfilehash: 065f71e45c2a56dbaa16a45f70958ca3dea80c48
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790834"
---
# <a name="icordebugvirtualunwinder-interface"></a>Interface ICorDebugVirtualUnwinder
Fornece métodos para ajudar no desenrolamento de pilha.  
  
## <a name="methods"></a>{1&gt;Métodos&lt;1}  
  
|Método|Name|  
|------------|----------|  
|[Método GetContext](icordebugvirtualunwinder-getcontext-method.md)|Obtém o contexto atual deste desenrolador.|  
|[Método Next](icordebugvirtualunwinder-next-method.md)|Avança para o contexto do chamador.|  
  
## <a name="remarks"></a>Comentários  
 Os membros da interface `ICorDebugVirtualUnwinder` são implementados pelo depurador para ajudar no desenrolamento de pilha.  
  
> [!NOTE]
> Essa interface está disponível somente com .NET Native. Se você implementar essa interface para cenários ICorDebug fora do .NET Native, o Common Language Runtime ignorará essa interface.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Depurando interfaces](debugging-interfaces.md)
- [Depuração](index.md)
