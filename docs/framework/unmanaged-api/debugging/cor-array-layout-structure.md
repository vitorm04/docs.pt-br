---
title: Estrutura COR_ARRAY_LAYOUT
ms.date: 03/30/2017
api_name:
- COR_ARRAY_LAYOUT
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_ARRAY_LAYOUT
helpviewer_keywords:
- COR_DEBUG_IL_TO_NATIVE_MAP structure [.NET Framework debugging]
ms.assetid: aa20ac3d-6f60-4aa2-91c5-f3a86f82eba8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a3a5a5bb26912c87cdf37ba0d8f0cee1cf1ffa97
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59142006"
---
# <a name="corarraylayout-structure"></a>Estrutura COR_ARRAY_LAYOUT
Fornece informações sobre o layout de um objeto matriz na memória.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef struct COR_ARRAY_LAYOUT {  
    COR_TYPEID componentID;  
    CorElementType componentType;  
    ULONG32 firstElementOffset;  
    ULONG32 elementSize;  
    ULONG32 countOffset;   
    ULONG32 rankSize;   
    ULONG32 numRanks;   
    ULONG32 rankOffset;   
} COR_ARRAY_LAYOUT;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`componentID`|O identificador do tipo de objetos que contém a matriz.|  
|`componentType`|Um valor de enumeração CorElementType que indica se o componente é uma referência de coleta de lixo, uma classe de valor ou um primitivo.|  
|`firstElementOffset`|O deslocamento para o primeiro elemento na matriz.|  
|`elementSize`|O tamanho de cada elemento.|  
|`countOffset`|O deslocamento para o número de elementos na matriz.|  
|`rankSize`|O tamanho de classificação, em bytes.|  
|`numRanks`|O número de classificações na matriz.|  
|`rankOffset`|O deslocamento no qual iniciar as classificações.|  
  
## <a name="remarks"></a>Comentários  
 O `rankSize` campo especifica o tamanho de uma classificação em uma matriz multidimensional. É preciso para matrizes unidimensionais também.  
  
 O valor de `numRanks` é 1 para uma matriz unidimensional e `N` para uma matriz multidimensional de `N` dimensões.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Estruturas de depuração](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [Depuração](../../../../docs/framework/unmanaged-api/debugging/index.md)
