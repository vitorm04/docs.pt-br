---
title: Enumeração COR_PRF_GC_ROOT_FLAGS
ms.date: 03/30/2017
api_name:
- COR_PRF_GC_ROOT_FLAGS
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_ROOT_FLAGS
helpviewer_keywords:
- COR_PRF_GC_ROOT_FLAGS enumeration [.NET Framework profiling]
ms.assetid: 4611ee6f-0f05-4d84-91e1-e83d5e7dd7e4
topic_type:
- apiref
ms.openlocfilehash: 174486a88192bd5ff11074930d5ad3375603f8a5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449462"
---
# <a name="cor_prf_gc_root_flags-enumeration"></a>Enumeração COR_PRF_GC_ROOT_FLAGS
Indica uma propriedade de uma raiz de coleta de lixo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
typedef enum {  
    COR_PRF_GC_ROOT_PINNING = 0x1,  
    COR_PRF_GC_ROOT_WEAKREF = 0x2,  
    COR_PRF_GC_ROOT_INTERIOR = 0x4,  
    COR_PRF_GC_ROOT_REFCOUNTED = 0x8,  
} COR_PRF_GC_ROOT_FLAGS;  
```  
  
## <a name="members"></a>Membros  
  
|{1&gt;Membro&lt;1}|Descrição|  
|------------|-----------------|  
|`COR_PRF_GC_ROOT_PINNING`|A raiz impede que uma coleta de lixo mova o objeto.|  
|`COR_PRF_GC_ROOT_WEAKREF`|A raiz não impede a coleta de lixo.|  
|`COR_PRF_GC_ROOT_INTERIOR`|A raiz refere-se a um campo do objeto em vez do próprio objeto.|  
|`COR_PRF_GC_ROOT_REFCOUNTED`|A raiz impedirá a coleta de lixo se a contagem de referência do objeto for um determinado valor.|  
  
## <a name="remarks"></a>Comentários  
 `COR_PRF_GC_ROOT_FLAGS` é um bitmask que fornece informações adicionais sobre raízes especiais. No entanto, nem todas as raízes são especiais. Por exemplo, algumas raízes não são referências fracas, ponteiros interiores, fixados ou contados por referência. Para essas raízes, não há nenhum sinalizador para transmitir. Portanto, os métodos que usam essa enumeração, como o método [ICorProfilerCallback2:: RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) , enviam 0 para o bitmask dos sinalizadores, indicando que todos os sinalizadores estão desativados.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Criando perfil de enumerações](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
