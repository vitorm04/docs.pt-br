---
title: Método ICorProfilerInfo2::GetObjectGeneration
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetObjectGeneration
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetObjectGeneration
helpviewer_keywords:
- GetObjectGeneration method [.NET Framework profiling]
- ICorProfilerInfo2::GetObjectGeneration method [.NET Framework profiling]
ms.assetid: b0d25f76-0bd5-4aa6-96cf-bfec0e1de28b
topic_type:
- apiref
ms.openlocfilehash: b75de955e3b6857c9cc1b5411df4b0f262c4cb9a
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862688"
---
# <a name="icorprofilerinfo2getobjectgeneration-method"></a>Método ICorProfilerInfo2::GetObjectGeneration
Obtém o segmento do heap que contém o objeto especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetObjectGeneration(  
    [in] ObjectID objectId,  
    [out] COR_PRF_GC_GENERATION_RANGE *range);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `objectId`  
 no A ID do objeto.  
  
 `range`  
 fora Um ponteiro para uma estrutura de [COR_PRF_GC_GENERATION_RANGE](cor-prf-gc-generation-range-structure.md) , que descreve um intervalo (ou seja, um bloco) de memória na geração que está passando pela coleta de lixo. Este intervalo contém o objeto especificado.  
  
## <a name="remarks"></a>Comentários  
 O método `GetObjectGeneration` pode ser chamado de qualquer retorno de chamada do criador de perfil, desde que a coleta de lixo não esteja em andamento. Ou seja, ele pode ser chamado de qualquer retorno de chamada, exceto aqueles que ocorrem entre [ICorProfilerCallback2:: GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md) e [ICorProfilerCallback2:: GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md).  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorProfilerInfo](icorprofilerinfo-interface.md)
- [Interface ICorProfilerInfo2](icorprofilerinfo2-interface.md)
