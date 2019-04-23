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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 263c22a07f363c2752afb50779515de043976e93
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59207702"
---
# <a name="corprfgcrootflags-enumeration"></a>Enumeração COR_PRF_GC_ROOT_FLAGS
Indica uma propriedade de uma raiz de coleta de lixo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef enum {  
    COR_PRF_GC_ROOT_PINNING = 0x1,  
    COR_PRF_GC_ROOT_WEAKREF = 0x2,  
    COR_PRF_GC_ROOT_INTERIOR = 0x4,  
    COR_PRF_GC_ROOT_REFCOUNTED = 0x8,  
} COR_PRF_GC_ROOT_FLAGS;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`COR_PRF_GC_ROOT_PINNING`|A raiz impede que uma coleta de lixo mova o objeto.|  
|`COR_PRF_GC_ROOT_WEAKREF`|A raiz não impede a coleta de lixo.|  
|`COR_PRF_GC_ROOT_INTERIOR`|A raiz refere-se a um campo de objeto em vez do próprio objeto.|  
|`COR_PRF_GC_ROOT_REFCOUNTED`|A raiz impede a coleta de lixo se a contagem de referência do objeto é um valor determinado.|  
  
## <a name="remarks"></a>Comentários  
 `COR_PRF_GC_ROOT_FLAGS` é um bitmask que fornece informações adicionais sobre raízes especiais. No entanto, nem todas as raízes são especiais. Por exemplo, alguns raízes não são referências fracas, ponteiros interiores, fixos ou contado por referência. Para tais raízes, não há nenhum sinalizador para transmitir. Portanto, os métodos que usam essa enumeração, como o [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) método, envio de 0 para a máscara de bits de sinalizadores, indicando que todos os sinalizadores são desativados.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Criando perfil de enumerações](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
