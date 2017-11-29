---
title: "Método ICorProfilerCallback::ObjectsAllocatedByClass"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ObjectsAllocatedByClass
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ObjectsAllocatedByClass
helpviewer_keywords:
- ObjectsAllocatedByClass method [.NET Framework profiling]
- ICorProfilerCallback::ObjectsAllocatedByClass method [.NET Framework profiling]
ms.assetid: 91d688f3-a80e-419d-9755-ff94bc04188a
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 28c0ff537a5b2133bdeb1db8aeadf5545d8dfd0f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackobjectsallocatedbyclass-method"></a>Método ICorProfilerCallback::ObjectsAllocatedByClass
Notifica o criador de perfil sobre o número de instâncias de cada classe especificada que foram criados desde a coleta de lixo mais recente.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT ObjectsAllocatedByClass(  
    [in] ULONG   cClassCount,  
    [in, size_is(cClassCount)] ClassID classIds[] ,  
    [in, size_is(cClassCount)] ULONG   cObjects[] );  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `cClassCount`  
 [in] O tamanho do `classIds` e `cObjects` matrizes.  
  
 `classIds`  
 [in] Uma matriz de IDs, onde cada ID Especifica uma classe com uma ou mais instâncias de classe.  
  
 `cObjects`  
 [in] Uma matriz de inteiros, onde cada inteiro Especifica o número de instâncias da classe correspondente na `classIds` matriz.  
  
## <a name="remarks"></a>Comentários  
 O `classIds` e `cObjects` as matrizes são matrizes paralelos. Por exemplo, `classIds[i]` e `cObjects[i]` a mesma classe de referência. Se nenhuma instância de uma classe tiver sido criada desde a coleta de lixo anterior, a classe é omitida. O `ObjectsAllocatedByClass` retorno de chamada não relatarão objetos alocados no heap de objeto grande.  
  
 Os números relatados pelo `ObjectsAllocatedByClass` são apenas estimativas. Para contagens exatas, use [: ObjectAllocated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md).  
  
 O `classIds` matriz pode conter uma ou mais entradas nulas se correspondente `cObjects` matriz tem tipos estão descarregando.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
