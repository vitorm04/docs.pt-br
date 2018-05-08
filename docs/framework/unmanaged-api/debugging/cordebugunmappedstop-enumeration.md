---
title: Enumeração CorDebugUnmappedStop
ms.date: 03/30/2017
api_name:
- CorDebugUnmappedStop
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugUnmappedStop
helpviewer_keywords:
- CorDebugUnmappedStop enumeration [.NET Framework debugging]
ms.assetid: a684f7d7-d0c2-4690-b721-639e613f11f8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0d812a452910913f169d4377bafa82e823c533d6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="cordebugunmappedstop-enumeration"></a>Enumeração CorDebugUnmappedStop
Especifica o tipo de código não mapeado que pode disparar uma interrupção na execução do código pelo passador.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef enum CorDebugUnmappedStop {  
    STOP_NONE               = 0x0,  
    STOP_PROLOG             = 0x01,  
    STOP_EPILOG             = 0x02,  
    STOP_NO_MAPPING_INFO    = 0x04,  
    STOP_OTHER_UNMAPPED     = 0x08,  
    STOP_UNMANAGED          = 0x10,  
    STOP_ALL                = 0xffff,  
} CorDebugUnmappedStop;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`STOP_NONE`|Não pare em qualquer tipo de código não mapeado.|  
|`STOP_PROLOG`|Pare no código de prólogo.|  
|`STOP_EPILOG`|Pare no código de epílogo.|  
|`STOP_NO_MAPPING_INFO`|Pare no código que não tem nenhuma informação de mapeamento.|  
|`STOP_OTHER_UNMAPPED`|Pare em código não mapeado que não cabe no prólogo, epílogo, informações de mapeamento não ou categoria não gerenciada.|  
|`STOP_UNMANAGED`|Pare em código não gerenciado. Esse valor é válido somente com depuração interop.|  
|`STOP_ALL`|Pare em todos os tipos de código não mapeado.|  
  
## <a name="remarks"></a>Comentários  
 Use o [: Setunmappedstopmask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) método para definir os sinalizadores que especificam o código não mapeado no qual o seletor irá parar.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Declarando enumerações](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
