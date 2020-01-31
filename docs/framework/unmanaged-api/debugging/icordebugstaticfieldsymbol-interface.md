---
title: Interface ICorDebugStaticFieldSymbol
ms.date: 03/30/2017
ms.assetid: c0b93609-631e-4b15-878a-189ede922631
ms.openlocfilehash: b50b9c8435f19e1a77229f01dc85514f5f75c9f5
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791797"
---
# <a name="icordebugstaticfieldsymbol-interface"></a>Interface ICorDebugStaticFieldSymbol
Representa as informações de símbolo de depuração de um campo estático.  
  
## <a name="methods"></a>{1&gt;Métodos&lt;1}  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método GetAddress](icordebugstaticfieldsymbol-getaddress-method.md)|Obtém o endereço do campo estático.|  
|[Método GetName](icordebugstaticfieldsymbol-getname-method.md)|Obtém o nome do campo estático.|  
|[Método GetSize](icordebugstaticfieldsymbol-getsize-method.md)|Obtém o tamanho em bytes do campo estático.|  
  
## <a name="remarks"></a>Comentários  
 A interface `ICorDebugStaticFieldSymbol` é usada para recuperar as informações de símbolo de depuração para um campo estático.  
  
> [!NOTE]
> Essa interface está disponível somente com .NET Native. Se você implementar essa interface para cenários ICorDebug fora do .NET Native, o Common Language Runtime ignorará essa interface.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorDebugInstanceFieldSymbol](icordebuginstancefieldsymbol-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
- [Depuração](index.md)
