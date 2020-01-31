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
ms.openlocfilehash: 4eff8472e353c4e5fd2505b281cc9efc89f013fc
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867200"
---
# <a name="cor_prf_gc_generation-enumeration"></a>Enumeração COR_PRF_GC_GENERATION
Identifica uma geração de coleta de lixo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
typedef enum {  
    COR_PRF_GC_GEN_0 = 0,  
    COR_PRF_GC_GEN_1 = 1,  
    COR_PRF_GC_GEN_2 = 2,  
    COR_PRF_GC_LARGE_OBJECT_HEAP = 3  
} COR_PRF_GC_GENERATION;  
```  
  
## <a name="members"></a>Membros  
  
|{1&gt;Membro&lt;1}|Descrição|  
|------------|-----------------|  
|`COR_PRF_GC_GEN_0`|O objeto é armazenado como geração 0.|  
|`COR_PRF_GC_GEN_1`|O objeto é armazenado como geração 1.|  
|`COR_PRF_GC_GEN_2`|O objeto é armazenado como geração 2.|  
|`COR_PRF_GC_LARGE_OBJECT_HEAP`|O objeto é armazenado no heap de objeto grande.|  
  
## <a name="remarks"></a>Comentários  
 O coletor de lixo melhora o desempenho de gerenciamento de memória dividindo objetos em gerações com base na idade. O coletor de lixo atualmente usa três gerações, numeradas de 0, 1 e 2, além de um segmento de heap especial que é usado para objetos grandes. Objetos cujo tamanho é maior do que um valor específico são armazenados no heap de objeto grande. Outros objetos alocados começam a pertencer à geração 0. Todos os objetos que existem após a coleta de lixo ocorre na geração 0 são promovidos para a geração 1. Os objetos que existem após a coleta de lixo ocorrem na passagem de geração 1 para a geração 2.  
  
 O uso de gerações significa que o coletor de lixo tem que trabalhar apenas com um subconjunto dos objetos alocados a qualquer momento.  
  
 A enumeração de `COR_PRF_GC_GENERATION` é usada pela estrutura de [COR_PRF_GC_GENERATION_RANGE](cor-prf-gc-generation-range-structure.md) .  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Criando perfil de enumerações](profiling-enumerations.md)
