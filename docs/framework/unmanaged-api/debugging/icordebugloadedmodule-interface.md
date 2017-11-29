---
title: Interface ICorDebugLoadedModule
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 34be6369-2e75-4a95-a538-3b29ac97cf6d
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5cdc89ec81d76a3ce7d39a53e097745d6c9822f8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
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
 O `ICorDebugLoadedModule` interface é implementada por um depurador e é usado pelo CLR interfaces de depuração para obter informações sobre o módulo carregado do depurador.  
  
> [!NOTE]
>  Esta interface só está disponível com o .NET Native. Se você implementar essa interface para cenários de ICorDebug fora do .NET nativo, o common language runtime irá ignorar essa interface.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de depuração](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Depuração](../../../../docs/framework/unmanaged-api/debugging/index.md)
