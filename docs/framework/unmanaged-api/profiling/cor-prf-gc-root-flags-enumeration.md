---
title: "Enumeração COR_PRF_GC_ROOT_FLAGS"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_PRF_GC_ROOT_FLAGS
api_location: mscorwks.dll
api_type: COM
f1_keywords: COR_PRF_GC_ROOT_FLAGS
helpviewer_keywords: COR_PRF_GC_ROOT_FLAGS enumeration [.NET Framework profiling]
ms.assetid: 4611ee6f-0f05-4d84-91e1-e83d5e7dd7e4
topic_type: apiref
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f340f9ad83d28b00054a0997bf4b60c750192bef
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
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
|`COR_PRF_GC_ROOT_PINNING`|A raiz impede uma coleta de lixo de mover o objeto.|  
|`COR_PRF_GC_ROOT_WEAKREF`|A raiz não impede que a coleta de lixo.|  
|`COR_PRF_GC_ROOT_INTERIOR`|A raiz refere-se a um campo do objeto, em vez do próprio objeto.|  
|`COR_PRF_GC_ROOT_REFCOUNTED`|A raiz impede que a coleta de lixo se a contagem de referência do objeto é um determinado valor.|  
  
## <a name="remarks"></a>Comentários  
 `COR_PRF_GC_ROOT_FLAGS`é um bitmask que fornece informações adicionais sobre raízes especiais. No entanto, nem todas as raízes são especiais. Por exemplo, alguns raízes não são referências fracas, ponteiros internos, fixos ou contado por referência. Para tal raízes, não há nenhum sinalizador para transmitir. Portanto, os métodos que usam essa enumeração, como o [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) método send 0 para a máscara de bits de sinalizadores indicando que todos os sinalizadores são desativados.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
