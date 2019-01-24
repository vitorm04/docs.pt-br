---
title: Enumeração CorDebugStateChange
ms.date: 03/30/2017
api_name:
- CorDebugStateChange
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 1d4424ab-5143-4e50-a84a-ceeb4ddf3bba
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0f0f692b692628d50755ce813c66823f940dccb8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54513771"
---
# <a name="cordebugstatechange-enumeration"></a>Enumeração CorDebugStateChange
Descreve a quantidade de dados armazenados em cache que devem ser descartados com base em alterações no processo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef enum CorDebugStateChange  
{  
    PROCESS_RUNNING = 0x0000001,   
    FLUSH_ALL       = 0x0000002,   
} CorDebugStateChange;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`PROCESS_RUNNING`|O processo atingiu um novo estado de memória por meio da execução do encaminhamento.|  
|`SET_CONTEXT_FLAG_UNWIND_FRAME`|A memória do processo pode ser arbitrariamente diferente do que era anteriormente.|  
  
## <a name="remarks"></a>Comentários  
 Um membro do `CorDebugStateChange` enumeração é fornecida como um argumento quando o depurador chama o [ProcessStateChanged](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md) método  
  
> [!NOTE]
>  Essa enumeração destina-se para uso no .NET Native somente para cenários de depuração.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Declarando enumerações](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [Depuração](../../../../docs/framework/unmanaged-api/debugging/index.md)
