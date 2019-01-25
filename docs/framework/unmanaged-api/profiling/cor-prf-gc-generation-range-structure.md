---
title: Estrutura COR_PRF_GC_GENERATION_RANGE
ms.date: 03/30/2017
api_name:
- COR_PRF_GC_GENERATION_RANGE
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_GENERATION_RANGE
helpviewer_keywords:
- COR_PRF_GC_GENERATION_RANGE structure [.NET Framework profiling]
ms.assetid: e7e07273-8d10-4a68-807e-59634e3f8c5e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bbeebc766d6e8048843a74691addd1dee90623ee
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54621690"
---
# <a name="corprfgcgenerationrange-structure"></a>Estrutura COR_PRF_GC_GENERATION_RANGE
Descreve um intervalo (ou seja, um bloco) de memória que está passando por coleta de lixo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef struct COR_PRF_GC_GENERATION_RANGE {  
    COR_PRF_GC_GENERATION generation;  
    ObjectID rangeStart;  
    UINT_PTR rangeLength;  
    UINT_PTR rangeLengthReserved;  
} COR_PRF_GC_GENERATION_RANGE;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`generation`|Um valor igual a [COR_PRF_GC_GENERATION](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md) enumeração que especifica a geração para o qual o bloco de memória pertence.|  
|`rangeStart`|A ID de um objeto que especifica o local de início do bloco de memória.|  
|`rangeLength`|Um ponteiro para um inteiro que especifica o tamanho da parte usada do bloco de memória (ou seja, a quantidade de memória usada dentro do bloco).|  
|`rangeLengthReserved`|Um ponteiro para um inteiro que especifica o tamanho do bloco de memória (ou seja, a quantidade de memória reservada para o bloco).|  
  
## <a name="remarks"></a>Comentários  
 O `rangeLength` valor é garantido que seja preciso apenas se [ICorProfilerInfo2::GetGenerationBounds](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getgenerationbounds-method.md) ou [ICorProfilerInfo2::GetObjectGeneration](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getobjectgeneration-method.md), ambas que usam o `COR_PRF_GC_GENERATION_RANGE` estrutura, é chamado a partir de [ICorProfilerCallback2::GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md) ou o [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) método.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Estruturas de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
