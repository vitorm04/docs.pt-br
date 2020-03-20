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
ms.openlocfilehash: 4c79d0e4e37f3f884651e49c8fff6db72fac4f50
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179301"
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
|`oldOffset`|A antiga linguagem intermediária da Microsoft (MSIL) compensou em relação ao início da função.|  
|`newOffset`|O novo Deslocamento mSIL em relação ao início da função.|  
|`fAccurate`|`true`se o mapeamento for conhecido como preciso; caso contrário, `false`.|  
  
## <a name="remarks"></a>Comentários  
 O formato do mapa é o seguinte: O `oldOffset` depurador assumirá que se refere a uma compensação MSIL dentro do código MSIL original e não modificado. O `newOffset` parâmetro refere-se ao deslocamento MSIL correspondente dentro do novo código instrumentado.  
  
 Para que o passo funcione corretamente, os seguintes requisitos devem ser atendidos:  
  
- O mapa deve ser classificado em ordem ascendente.  
  
- O código MSIL instrumentado não deve ser reordenado.  
  
- O código MSIL original não deve ser removido.  
  
- O mapa deve incluir entradas para mapear todos os pontos de seqüência do arquivo de banco de dados do programa (PDB).  
  
 O mapa não interpola entradas ausentes. O exemplo a seguir mostra um mapa e seus resultados.  
  
 Mapa:  
  
- 0 compensação antiga, 0 novo deslocamento  
  
- 5 deslocamento antigo, 10 novos deslocamentos  
  
- 9 antigos deslocamento, 20 novo deslocamento  
  
 Resultados:  
  
- Um antigo deslocamento de 0, 1, 2, 3 ou 4 será mapeado para um novo deslocamento de 0.  
  
- Um antigo deslocamento de 5, 6, 7 ou 8 será mapeado para novo offset 10.  
  
- Um antigo deslocamento de 9 ou mais será mapeado para novo offset 20.  
  
- Um novo deslocamento de 0, 1, 2, 3, 4, 5, 6, 7, 8 ou 9 será mapeado para o antigo deslocamento 0.  
  
- Um novo deslocamento de 10, 11, 12, 13, 14, 15, 16, 17, 18 ou 19 será mapeado para o antigo offset 5.  
  
- Um novo deslocamento de 20 ou mais será mapeado para o antigo offset 9.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorProf.idl  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Estruturas de depuração](debugging-structures.md)
- [Depuração](index.md)
