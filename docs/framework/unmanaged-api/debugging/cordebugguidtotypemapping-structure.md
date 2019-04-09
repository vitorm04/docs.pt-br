---
title: Estrutura CorDebugGuidToTypeMapping
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- CorDebugGuidToTypeMapping
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugGuidToTypeMapping
helpviewer_keywords:
- CorDebugGuidToTypeMapping structure [.NET Framework debugging]
ms.assetid: 57dbccd9-b16d-4da3-ae25-7a2cf9adf679
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9dc7093edaf12e801a1e1adc52b0be823ff92b91
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59079910"
---
# <a name="cordebugguidtotypemapping-structure"></a>Estrutura CorDebugGuidToTypeMapping
Mapeia um [!INCLUDE[wrt](../../../../includes/wrt-md.md)] GUID para seu objeto correspondente do ICorDebugType.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
typedef struct CorDebugGuidToTypeMapping {  
    GUID iid;  
    ICorDebugType *pType;  
} CorDebugGuidToTypeMapping;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`iid`|O GUID do cache no [!INCLUDE[wrt](../../../../includes/wrt-md.md)] tipo.|  
|`pType`|Um ponteiro para um objeto ICorDebugType que fornece informações sobre o tipo de cache.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)].  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Estruturas de depuração](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [Depuração](../../../../docs/framework/unmanaged-api/debugging/index.md)
