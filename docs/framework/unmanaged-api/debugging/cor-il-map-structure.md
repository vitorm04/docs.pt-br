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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9676730a4f11ed77996b7a4aab4e538aba9b53c4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33407356"
---
# <a name="corilmap-structure"></a>Estrutura COR_IL_MAP
Especifica mudanças no deslocamento relativo de uma função.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef struct _COR_IL_MAP {  
    ULONG32 oldOffset;   
    ULONG32 newOffset;   
    BOOL    fAccurate;  
} COR_IL_MAP;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`oldOffset`|O antigo Microsoft intermediate language (MSIL) deslocamento relativo ao início da função.|  
|`newOffset`|O deslocamento MSIL novo relativo ao início da função.|  
|`fAccurate`|`true` Se o mapeamento é conhecido por ser preciso; Caso contrário, `false`.|  
  
## <a name="remarks"></a>Comentários  
 O formato do mapa é da seguinte maneira: O depurador assumirá que `oldOffset` refere-se a um deslocamento MSIL dentro do código MSIL original, não modificado. O `newOffset` parâmetro refere-se para o deslocamento MSIL correspondente no código instrumentado, novo.  
  
 Para passar para funcionar corretamente, os seguintes requisitos devem ser atendidos:  
  
-   O mapa deve ser classificado em ordem crescente.  
  
-   Não deve ser reordenado código MSIL instrumentado.  
  
-   Código MSIL original não deve ser removido.  
  
-   O mapa deve incluir as entradas para todos os pontos de sequência do arquivo de programa (PDB) de banco de dados do mapa.  
  
 O mapa não interpolar entradas ausentes. O exemplo a seguir mostra um mapa e seus resultados.  
  
 Mapa:  
  
-   deslocamento antigo 0, 0 deslocamento novo  
  
-   deslocamento antigo 5, 10 deslocamento novo  
  
-   deslocamento antigo 9, 20 de deslocamento de novo  
  
 Resultados:  
  
-   Um deslocamento antigo de 0, 1, 2, 3 ou 4 será mapeado para um novo deslocamento de 0.  
  
-   Um deslocamento antigo de 5, 6, 7 ou 8 será mapeado para o novo deslocamento de 10.  
  
-   Um deslocamento antigo de 9 ou superior será mapeado para o novo deslocamento 20.  
  
-   Um novo deslocamento de 0, 1, 2, 3, 4, 5, 6, 7, 8 ou 9 será mapeado para o antigo deslocamento de 0.  
  
-   Um novo deslocamento de 10, 11, 12, 13, 14, 15, 16, 17, 18 ou 19 será mapeado para o deslocamento antigo 5.  
  
-   Um novo deslocamento de 20 ou maior será mapeado para deslocamento antigo 9.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, Corprof. idl  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Estruturas de depuração](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [Depuração](../../../../docs/framework/unmanaged-api/debugging/index.md)
