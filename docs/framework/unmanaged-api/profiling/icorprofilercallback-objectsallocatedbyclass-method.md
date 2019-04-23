---
title: Método ICorProfilerCallback::ObjectsAllocatedByClass
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ObjectsAllocatedByClass
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ObjectsAllocatedByClass
helpviewer_keywords:
- ObjectsAllocatedByClass method [.NET Framework profiling]
- ICorProfilerCallback::ObjectsAllocatedByClass method [.NET Framework profiling]
ms.assetid: 91d688f3-a80e-419d-9755-ff94bc04188a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b9f5d2c08abbcab6bc1a6d0569b8e70d7c919def
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59195859"
---
# <a name="icorprofilercallbackobjectsallocatedbyclass-method"></a>Método ICorProfilerCallback::ObjectsAllocatedByClass
Notifica o criador de perfil sobre o número de instâncias de cada classe especificada que foram criados desde a última coleta de lixo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT ObjectsAllocatedByClass(  
    [in] ULONG   cClassCount,  
    [in, size_is(cClassCount)] ClassID classIds[] ,  
    [in, size_is(cClassCount)] ULONG   cObjects[] );  
```  
  
## <a name="parameters"></a>Parâmetros  
 `cClassCount`  
 [in] O tamanho do `classIds` e `cObjects` matrizes.  
  
 `classIds`  
 [in] Uma matriz de IDs, onde cada ID Especifica uma classe com uma ou mais instâncias de classe.  
  
 `cObjects`  
 [in] Uma matriz de inteiros, onde cada inteiro Especifica o número de instâncias da classe correspondente no `classIds` matriz.  
  
## <a name="remarks"></a>Comentários  
 O `classIds` e `cObjects` matrizes são matrizes paralelas. Por exemplo, `classIds[i]` e `cObjects[i]` fazer referência à mesma classe. Se nenhuma instância de uma classe tiver sido criada desde a coleta de lixo anterior, a classe é omitida. O `ObjectsAllocatedByClass` retorno de chamada não relatará objetos alocados no heap de objeto grande.  
  
 Os números relatados pelo `ObjectsAllocatedByClass` são apenas estimativas. Para a contagem exata, use [ICorProfilerCallback:: ObjectAllocated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md).  
  
 O `classIds` matriz pode conter um ou mais entradas nulas se correspondente `cObjects` matriz tem tipos estão descarregando.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
