---
title: "Enumeração CorDebugMappingResult"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugMappingResult
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugMappingResult
helpviewer_keywords: CorDebugMappingResult enumeration [.NET Framework debugging]
ms.assetid: 701281dd-2936-45c8-a1f0-3bf7332b093b
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 793158ef63a0de27786dc8bd9b306f10c228054e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="cordebugmappingresult-enumeration"></a>Enumeração CorDebugMappingResult
Fornece os detalhes sobre como o valor do ponteiro de instrução (IP) foi obtido.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef enum CorDebugMappingResult {  
    MAPPING_PROLOG              = 0x1,  
    MAPPING_EPILOG              = 0x2,  
    MAPPING_NO_INFO             = 0x4,  
    MAPPING_UNMAPPED_ADDRESS    = 0x8,  
    MAPPING_EXACT               = 0x10,  
    MAPPING_APPROXIMATE         = 0x20,  
} CorDebugMappingResult;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`MAPPING_PROLOG`|O código nativo está no prólogo, portanto, o valor do IP é 0.|  
|`MAPPING_EPILOG`|O código nativo está em um epílogo, portanto, o valor do IP é o endereço da última instrução do método.|  
|`MAPPING_NO_INFO`|Nenhuma informação de mapeamento está disponível para o método, portanto, o valor do IP é 0.|  
|`MAPPING_UNMAPPED_ADDRESS`|Embora não haja informações de mapeamento para o método, o endereço atual não pode ser mapeado para o código Microsoft intermediate language (MSIL). O valor do IP é 0.|  
|`MAPPING_EXACT`|O método mapeia exatamente ao código MSIL tanto o quadro foi interpretado, portanto, o valor do IP é preciso.|  
|`MAPPING_APPROXIMATE`|O método foi mapeado com êxito, mas o valor do IP pode ser aproximado.|  
  
## <a name="remarks"></a>Comentários  
 Você pode usar o [Icordebugilframe](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getip-method.md) método para obter o valor do ponteiro de instrução.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Declarando enumerações](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
