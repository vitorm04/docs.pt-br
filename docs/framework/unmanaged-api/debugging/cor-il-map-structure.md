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
ms.openlocfilehash: c7452b76509d5eca592cc3b95df1f77703ec1111
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54561823"
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
|`oldOffset`|O antigo deslocamento Microsoft intermediate language (MSIL) em relação ao início da função.|  
|`newOffset`|O novo deslocamento MSIL relativo ao início da função.|  
|`fAccurate`|`true` Se o mapeamento é conhecido por ser preciso; Caso contrário, `false`.|  
  
## <a name="remarks"></a>Comentários  
 O formato do mapa é da seguinte maneira: O depurador pressupor que `oldOffset` refere-se a um deslocamento MSIL dentro do código MSIL original, sem modificações. O `newOffset` parâmetro refere-se para o deslocamento do MSIL correspondente dentro do código novo, instrumentado.  
  
 Para depuração funcione corretamente, os seguintes requisitos devem ser atendidos:  
  
-   O mapa deve ser classificado em ordem crescente.  
  
-   Código MSIL instrumentado não deve ser reordenado.  
  
-   Código MSIL original não deve ser removido.  
  
-   O mapa deve incluir as entradas para mapear todos os pontos de sequência do arquivo de banco de dados (PDB) do programa.  
  
 O mapa não interpola entradas ausentes. O exemplo a seguir mostra um mapa e seus resultados.  
  
 Mapear:  
  
-   deslocamento antigo 0, o novo deslocamento 0  
  
-   deslocamento antigo 5, 10 novo deslocamento  
  
-   deslocamento antigo 9, 20 novo deslocamento  
  
 Resultados:  
  
-   Um deslocamento antigo de 0, 1, 2, 3 ou 4 será mapeado para um novo deslocamento de 0.  
  
-   Um deslocamento antigo de 5, 6, 7 ou 8 será mapeado para o novo deslocamento de 10.  
  
-   Um deslocamento antigo de 9 ou superior será mapeado para o novo deslocamento 20.  
  
-   Um novo deslocamento de 0, 1, 2, 3, 4, 5, 6, 7, 8 ou 9 será mapeado para o deslocamento antigo 0.  
  
-   Um novo deslocamento de 10, 11, 12, 13, 14, 15, 16, 17, 18 ou 19 será mapeado para o deslocamento antigo 5.  
  
-   Um novo deslocamento de 20 ou superior será mapeado para o deslocamento antigo 9.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorProf.idl  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Estruturas de depuração](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [Depuração](../../../../docs/framework/unmanaged-api/debugging/index.md)
