---
title: "Enumeração COR_PRF_GC_GENERATION"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_PRF_GC_GENERATION
api_location: mscorwks.dll
api_type: COM
f1_keywords: COR_PRF_GC_GENERATION
helpviewer_keywords: COR_GC_GENERATION_FLAGS enumeration [.NET Framework profiling]
ms.assetid: d6ece160-26ad-4d39-abd7-05acd6f78c48
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 69eec0c2dfccacee4c54c9f2493da523812259aa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="corprfgcgeneration-enumeration"></a>Enumeração COR_PRF_GC_GENERATION
Identifica uma geração de coleta de lixo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef enum {  
    COR_PRF_GC_GEN_0 = 0,  
    COR_PRF_GC_GEN_1 = 1,  
    COR_PRF_GC_GEN_2 = 2,  
    COR_PRF_GC_LARGE_OBJECT_HEAP = 3  
} COR_PRF_GC_GENERATION;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`COR_PRF_GC_GEN_0`|O objeto é armazenado como geração 0.|  
|`COR_PRF_GC_GEN_1`|O objeto é armazenado como geração 1.|  
|`COR_PRF_GC_GEN_2`|O objeto é armazenado como geração 2.|  
|`COR_PRF_GC_LARGE_OBJECT_HEAP`|O objeto é armazenado no heap de objeto grande.|  
  
## <a name="remarks"></a>Comentários  
 O coletor de lixo melhora o desempenho de gerenciamento de memória por objetos separam em gerações com base na idade. O coletor de lixo atualmente usa três gerações, numeradas de 0, 1 e 2, além de um segmento de pilha especial que é usado para objetos grandes. Objetos cujo tamanho é maior que um valor específico são armazenados no heap de objeto grande. Outros objetos alocados começam pertencentes a geração 0. Todos os objetos que existem após a coleta de lixo na geração 0 são promovidos para a geração 1. Movem objetos existentes após a coleta de lixo na geração 1 na geração 2.  
  
 O uso de gerações significa que o coletor de lixo precisa trabalhar com apenas um subconjunto dos objetos alocados a qualquer momento.  
  
 O `COR_PRF_GC_GENERATION` enumeração é usada pelo [COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) estrutura.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Criando perfil de enumerações](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
