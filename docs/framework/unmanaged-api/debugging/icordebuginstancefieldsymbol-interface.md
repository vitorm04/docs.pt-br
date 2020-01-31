---
title: Interface ICorDebugInstanceFieldSymbol
ms.date: 03/30/2017
ms.assetid: a4a8f259-b83a-4425-ae8b-72b067dbc0d9
ms.openlocfilehash: 41258b0eeed5fbf8ab86546f74073f8eeaa3085c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777522"
---
# <a name="icordebuginstancefieldsymbol-interface"></a>Interface ICorDebugInstanceFieldSymbol
Representa as informações de símbolo de depuração de um campo de instância.  
  
## <a name="methods"></a>{1&gt;Métodos&lt;1}  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método GetName](icordebuginstancefieldsymbol-getname-method.md)|Obtém o nome do campo de instância.|  
|[Método GetOffset](icordebuginstancefieldsymbol-getoffset-method.md)|Obtém o deslocamento em bytes deste campo de instância em sua classe pai.|  
|[Método GetSize](icordebuginstancefieldsymbol-getsize-method.md)|Obtém o tamanho em bytes do campo de instância.|  
  
## <a name="remarks"></a>Comentários  
 A interface `ICorDebugInstanceFieldSymbol` é usada para recuperar as informações de símbolo de depuração para um campo de instância.  
  
> [!NOTE]
> Essa interface está disponível somente com .NET Native. Se você implementar essa interface para cenários ICorDebug fora do .NET Native, o Common Language Runtime ignorará essa interface.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorDebugStaticFieldSymbol](icordebugstaticfieldsymbol-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
- [Depuração](index.md)
