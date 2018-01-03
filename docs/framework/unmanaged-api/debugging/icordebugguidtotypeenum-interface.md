---
title: Interface ICorDebugGuidToTypeEnum
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugGuidToTypeEnum
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugGuidToTypeEnum
helpviewer_keywords: ICorDebugGuidToTypeEnum interface [.NET Framework debugging]
ms.assetid: aa32b12b-05fc-4ea8-a904-adae25034269
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9993a5aaaef3d5b83d21e3641029af12119188da
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugguidtotypeenum-interface"></a>Interface ICorDebugGuidToTypeEnum
Fornece um enumerador que define o mapeamento entre um conjunto de GUIDs e seus tipos correspondentes, são representados por instâncias de ICorDebugType. Esta interface herda os métodos da interface ICorDebugEnum.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Icordebugguidtotypeenum](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md)|Obtém o número especificado de [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) instâncias que mapeiam os GUIDs para informações de tipo.|  
  
## <a name="remarks"></a>Comentários  
 Um `ICorDebugGuidToTypeEnum` objeto de interface pode ser recuperado chamando o [Icordebugappdomain3](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) método. Um depurador pode chamar essa interface [próximo](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md) método para recuperar [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) gerenciados de objetos que representam os mapeamentos de representações de [!INCLUDE[wrt](../../../../includes/wrt-md.md)] tipos carregados do domínio do aplicativo usado para a chamada a [Icordebugappdomain3](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) método.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:**[!INCLUDE[wrt](../../../../includes/wrt-md.md)]  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
