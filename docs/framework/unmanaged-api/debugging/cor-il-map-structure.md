---
title: Estrutura COR_IL_MAP
ms.date: 03/30/2017
api_name:
- COR_IL_MAP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_IL_MAP
helpviewer_keywords:
- COR_IL_MAP structure [.NET Framework debugging]
ms.assetid: 534ebc17-963d-4b26-8375-8cd940281db3
topic_type:
- apiref
ms.openlocfilehash: c37f039d9636854c464e7981693c573bd60deab9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132341"
---
# <a name="cor_il_map-structure"></a>Estrutura COR_IL_MAP
Especifica mudanças no deslocamento relativo de uma função.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
typedef struct _COR_IL_MAP {  
    ULONG32 oldOffset;   
    ULONG32 newOffset;   
    BOOL    fAccurate;  
} COR_IL_MAP;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`oldOffset`|O antigo deslocamento da MSIL (Microsoft Intermediate Language) relativo ao início da função.|  
|`newOffset`|O novo deslocamento MSIL relativo ao início da função.|  
|`fAccurate`|`true` se é conhecido que o mapeamento seja preciso; caso contrário, `false`.|  
  
## <a name="remarks"></a>Comentários  
 O formato do mapa é o seguinte: o depurador irá supor que `oldOffset` se refere a um deslocamento MSIL dentro do código MSIL original e não modificado. O parâmetro `newOffset` refere-se ao deslocamento MSIL correspondente dentro do novo código instrumentado.  
  
 Para que a depuração funcione corretamente, os requisitos a seguir devem ser atendidos:  
  
- O mapa deve ser classificado em ordem crescente.  
  
- O código MSIL instrumentado não deve ser reordenado.  
  
- O código MSIL original não deve ser removido.  
  
- O mapa deve incluir entradas para mapear todos os pontos de sequência do arquivo de banco de dados do programa (PDB).  
  
 O mapa não interpola as entradas ausentes. O exemplo a seguir mostra um mapa e seus resultados.  
  
 Mapeada  
  
- 0 deslocamento antigo, 0 deslocamento novo  
  
- 5 deslocamento antigo, 10 novos deslocamentos  
  
- 9 deslocamento antigo, 20 deslocamento novo  
  
 Da  
  
- Um deslocamento antigo de 0, 1, 2, 3 ou 4 será mapeado para um novo deslocamento de 0.  
  
- Um deslocamento antigo de 5, 6, 7 ou 8 será mapeado para o novo deslocamento 10.  
  
- Um deslocamento antigo de 9 ou superior será mapeado para o novo deslocamento 20.  
  
- Um novo deslocamento de 0, 1, 2, 3, 4, 5, 6, 7, 8 ou 9 será mapeado para o deslocamento antigo 0.  
  
- Um novo deslocamento de 10, 11, 12, 13, 14, 15, 16, 17, 18 ou 19 será mapeado para o deslocamento antigo 5.  
  
- Um novo deslocamento de 20 ou mais será mapeado para o deslocamento antigo 9.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug. idl, CorProf. idl  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Estruturas de depuração](debugging-structures.md)
- [Depuração](index.md)
