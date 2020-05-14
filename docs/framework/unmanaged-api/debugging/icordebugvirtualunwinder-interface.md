---
title: Interface ICorDebugVirtualUnwinder
ms.date: 03/30/2017
ms.assetid: a09e9ccc-0b37-43e3-95c1-bc5fa7ee5f42
ms.openlocfilehash: 59ecf3da4b44af7b04dec26fbc3ea182c185d04a
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396447"
---
# <a name="icordebugvirtualunwinder-interface"></a>Interface ICorDebugVirtualUnwinder
Fornece métodos para ajudar no desenrolamento de pilha.  
  
## <a name="methods"></a>Métodos  
  
|Método|Nome|  
|------------|----------|  
|[Método GetContext](icordebugvirtualunwinder-getcontext-method.md)|Obtém o contexto atual deste desenrolador.|  
|[Método Next](icordebugvirtualunwinder-next-method.md)|Avança para o contexto do chamador.|  
  
## <a name="remarks"></a>Comentários  
 Os membros da `ICorDebugVirtualUnwinder` interface são implementados pelo depurador para ajudar no desenrolamento da pilha.  
  
> [!NOTE]
> Essa interface está disponível somente com .NET Native. Se você implementar essa interface para cenários ICorDebug fora do .NET Native, o Common Language Runtime ignorará essa interface.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Depurando interfaces](debugging-interfaces.md)
- [Depuração](index.md)
