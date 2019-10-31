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
ms.openlocfilehash: f37bf545553045b9737b7057feed78e1f06ace4d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099463"
---
# <a name="cor_array_layout-structure"></a>Estrutura COR_ARRAY_LAYOUT
Fornece informações sobre o layout de um objeto matriz na memória.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
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
|`componentID`|O identificador do tipo de objetos que a matriz contém.|  
|`componentType`|Um valor de enumeração CorElementType que indica se o componente é uma referência de coleta de lixo, uma classe de valor ou um primitivo.|  
|`firstElementOffset`|O deslocamento para o primeiro elemento na matriz.|  
|`elementSize`|O tamanho de cada elemento.|  
|`countOffset`|O deslocamento para o número de elementos na matriz.|  
|`rankSize`|O tamanho da classificação, em bytes.|  
|`numRanks`|O número de classificações na matriz.|  
|`rankOffset`|O deslocamento no qual as classificações começam.|  
  
## <a name="remarks"></a>Comentários  
 O campo `rankSize` especifica o tamanho de uma classificação em uma matriz multidimensional. Ele é preciso para matrizes unidimensionais também.  
  
 O valor de `numRanks` é 1 para uma matriz unidimensional e `N` para uma matriz multidimensional de dimensões `N`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Estruturas de depuração](debugging-structures.md)
- [Depuração](index.md)
