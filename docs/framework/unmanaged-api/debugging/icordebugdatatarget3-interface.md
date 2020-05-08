---
title: Interface ICorDebugDataTarget3
ms.date: 03/30/2017
ms.assetid: f477af85-994f-4df0-ae78-404ed252bf49
ms.openlocfilehash: 57ef9b567d57c77c523ca6daefcf80b1d7de66d1
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976402"
---
# <a name="icordebugdatatarget3-interface"></a>Interface ICorDebugDataTarget3
Estende logicamente a interface [ICorDebugDataTarget](icordebugdatatarget-interface.md) para fornecer informações sobre os módulos carregados.  
  
## <a name="method"></a>Método  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método GetLoadedModules](icordebugdatatarget3-getloadedmodules-method.md)|Obtém uma lista dos módulos que foram carregados até agora.|  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
> Essa interface está disponível somente com .NET Native. Se você implementar essa interface para cenários ICorDebug fora do .NET Native, o Common Language Runtime ignorará essa interface.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Depurando interfaces](debugging-interfaces.md)
- [Depuração](index.md)
