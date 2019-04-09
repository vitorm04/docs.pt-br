---
title: Interface ICorDebugDataTarget2
ms.date: 03/30/2017
ms.assetid: 13f11388-2f91-48d8-98d6-6a4a63cb5746
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7a74ba2b5c1dc2340d20a793bcf3b14e2af234b4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59149611"
---
# <a name="icordebugdatatarget2-interface"></a>Interface ICorDebugDataTarget2
Estende logicamente a [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)interface.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método CreateVirtualUnwinder](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-createvirtualunwinder-method.md)|Cria um novo unwinder de pilha que inicia o desenrolamento de um contexto inicial (que não é necessariamente folha de um thread).|  
|[Método EnumerateThreadIDs](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-enumeratethreadids-method.md)|Retorna uma lista de IDs de thread ativo.|  
|[Método GetImageFromPointer](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-getimagefrompointer-method.md)|Retorna o endereço base do módulo e o tamanho de um endereço no módulo.|  
|[Método GetImageLocation](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-getimagelocation-method.md)|Retorna o caminho de um módulo de endereço base do módulo.|  
|[Método GetSymbolProviderForImage](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-getsymbolproviderforimage-method.md)|Retorna o provedor de símbolo para um módulo do endereço base do módulo.|  
  
## <a name="remarks"></a>Comentários  
  
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
