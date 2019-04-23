---
title: Enumeração COR_PRF_GC_GENERATION
ms.date: 03/30/2017
api_name:
- COR_PRF_GC_GENERATION
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_GENERATION
helpviewer_keywords:
- COR_GC_GENERATION_FLAGS enumeration [.NET Framework profiling]
ms.assetid: d6ece160-26ad-4d39-abd7-05acd6f78c48
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0178e2a7877803644bb25e6700306d7ac2ef2d4f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59215882"
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
|`COR_PRF_GC_LARGE_OBJECT_HEAP`|O objeto é armazenado na heap de objeto grande.|  
  
## <a name="remarks"></a>Comentários  
 O coletor de lixo melhora o desempenho de gerenciamento de memória, divisão de objetos em gerações com base na idade. Atualmente, o coletor de lixo usa três gerações, numeradas de 0, 1 e 2, além de um segmento de heap especial que é usado para objetos grandes. Objetos cujo tamanho é maior do que um determinado valor são armazenados no heap de objeto grande. Outros objetos alocados começam que pertencem a geração 0. Todos os objetos que existem após a coleta de lixo na geração 0 são promovidos à geração 1. Movem objetos existentes após a coleta de lixo na geração 1 para a geração 2.  
  
 O uso de gerações significa que o coletor de lixo tem que trabalhar com apenas um subconjunto dos objetos alocados a qualquer momento.  
  
 O `COR_PRF_GC_GENERATION` enumeração é usada pelo [COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) estrutura.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Criando perfil de enumerações](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
