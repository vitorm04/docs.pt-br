---
title: "Enumeração CorDebugCreateProcessFlags"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugCreateProcessFlags
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugCreateProcessFlags
helpviewer_keywords: CorDebugCreateProcessFlags enumeration [.NET Framework debugging]
ms.assetid: e709acce-6a17-4346-b38a-467dba567358
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9e35aa2656a1e950cead94480eb06cde96e4c811
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugcreateprocessflags-enumeration"></a>Enumeração CorDebugCreateProcessFlags
Fornece opções adicionais de depuração que podem ser usadas em uma chamada para o [Icordebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) método.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef enum CorDebugCreateProcessFlags {  
    DEBUG_NO_SPECIAL_OPTIONS    = 0x0000  
} CorDebugCreateProcessFlags;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`DEBUG_NO_SPECIAL_OPTIONS`|Sem opções especiais são definidas.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Declarando enumerações](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
