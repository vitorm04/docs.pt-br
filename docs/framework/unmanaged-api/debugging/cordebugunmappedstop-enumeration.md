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
ms.openlocfilehash: c1cea8adcd12ecb3078e4469e6b018ed49064e0b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61723310"
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
|`STOP_PROLOG`|Interrompa no código de prólogo.|  
|`STOP_EPILOG`|Interrompa no código de epílogo.|  
|`STOP_NO_MAPPING_INFO`|Interrompa no código que não tem nenhuma informação de mapeamento.|  
|`STOP_OTHER_UNMAPPED`|Interrompa no código não mapeado que não se ajustam o prólogo, epílogo, nenhuma informação de mapeamento ou categoria não gerenciada.|  
|`STOP_UNMANAGED`|Pare em código não gerenciado. Esse valor é válido somente com depuração interop.|  
|`STOP_ALL`|Pare em todos os tipos de código não mapeado.|  
  
## <a name="remarks"></a>Comentários  
 Use o [ICorDebugStepper:: Setunmappedstopmask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) método para definir os sinalizadores que especificam o código não mapeado no qual o escalonador será interrompida.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Declarando enumerações](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
