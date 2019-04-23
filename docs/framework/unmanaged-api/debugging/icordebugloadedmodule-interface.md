---
title: Interface ICorDebugLoadedModule
ms.date: 03/30/2017
ms.assetid: 34be6369-2e75-4a95-a538-3b29ac97cf6d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6e91dda9cbc5957768e98db2b2a9e1026d94c03e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59200747"
---
# <a name="icordebugloadedmodule-interface"></a>Interface ICorDebugLoadedModule
Fornece informações sobre um módulo carregado.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método GetBaseAddress](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getbaseaddress-method.md)|Obtém o endereço base do módulo carregado.|  
|[Método GetName](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getname-method.md)|Obtém o nome do módulo carregado.|  
|[Método GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getsize-method.md)|Obtém o tamanho em bytes do módulo carregado.|  
  
## <a name="remarks"></a>Comentários  
 O `ICorDebugLoadedModule` interface é implementada por um depurador e é usado por interfaces de depuração CLR para obter informações sobre o módulo carregado a partir do depurador.  
  
> [!NOTE]
>  Essa interface só está disponível com o .NET Native. Se você implementar essa interface para cenários de ICorDebug fora do .NET nativo, o common language runtime irá ignorar essa interface.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Depuração](../../../../docs/framework/unmanaged-api/debugging/index.md)
