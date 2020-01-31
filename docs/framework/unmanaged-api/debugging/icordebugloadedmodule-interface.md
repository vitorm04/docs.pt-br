---
title: Interface ICorDebugLoadedModule
ms.date: 03/30/2017
ms.assetid: 34be6369-2e75-4a95-a538-3b29ac97cf6d
ms.openlocfilehash: 9d3bdcec9e90dab337b595294d114de4bd3d531f
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76781997"
---
# <a name="icordebugloadedmodule-interface"></a>Interface ICorDebugLoadedModule
Fornece informações sobre um módulo carregado.  
  
## <a name="methods"></a>{1&gt;Métodos&lt;1}  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método GetBaseAddress](icordebugloadedmodule-getbaseaddress-method.md)|Obtém o endereço base do módulo carregado.|  
|[Método GetName](icordebugloadedmodule-getname-method.md)|Obtém o nome do módulo carregado.|  
|[Método GetSize](icordebugloadedmodule-getsize-method.md)|Obtém o tamanho em bytes do módulo carregado.|  
  
## <a name="remarks"></a>Comentários  
 A interface `ICorDebugLoadedModule` é implementada por um depurador e é usada pelas interfaces de depuração CLR para obter informações sobre o módulo carregado do depurador.  
  
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
