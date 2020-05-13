---
title: Interface ICorDebugStaticFieldSymbol
ms.date: 03/30/2017
ms.assetid: c0b93609-631e-4b15-878a-189ede922631
ms.openlocfilehash: f9b82f0f98a668555a8096d7575c049c31cae93a
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379435"
---
# <a name="icordebugstaticfieldsymbol-interface"></a>Interface ICorDebugStaticFieldSymbol
Representa as informações de símbolo de depuração de um campo estático.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método GetAddress](icordebugstaticfieldsymbol-getaddress-method.md)|Obtém o endereço do campo estático.|  
|[Método GetName](icordebugstaticfieldsymbol-getname-method.md)|Obtém o nome do campo estático.|  
|[Método GetSize](icordebugstaticfieldsymbol-getsize-method.md)|Obtém o tamanho em bytes do campo estático.|  
  
## <a name="remarks"></a>Comentários  
 A `ICorDebugStaticFieldSymbol` interface é usada para recuperar as informações de símbolo de depuração para um campo estático.  
  
> [!NOTE]
> Essa interface está disponível somente com .NET Native. Se você implementar essa interface para cenários ICorDebug fora do .NET Native, o Common Language Runtime ignorará essa interface.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface ICorDebugInstanceFieldSymbol](icordebuginstancefieldsymbol-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
- [Depuração](index.md)
