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
ms.openlocfilehash: 9ba021ec223d00e57081567b76f70f59768e6b9a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445861"
---
# <a name="icorprofilercallbackobjectsallocatedbyclass-method"></a>Método ICorProfilerCallback::ObjectsAllocatedByClass
Notifica o criador de perfil sobre o número de instâncias de cada classe especificada que foram criadas desde a coleta de lixo mais recente.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT ObjectsAllocatedByClass(  
    [in] ULONG   cClassCount,  
    [in, size_is(cClassCount)] ClassID classIds[] ,  
    [in, size_is(cClassCount)] ULONG   cObjects[] );  
```  
  
## <a name="parameters"></a>Parâmetros  
 `cClassCount`  
 no O tamanho das matrizes `classIds` e `cObjects`.  
  
 `classIds`  
 no Uma matriz de IDs de classe, em que cada ID especifica uma classe com uma ou mais instâncias.  
  
 `cObjects`  
 no Uma matriz de inteiros, em que cada inteiro especifica o número de instâncias para a classe correspondente na matriz de `classIds`.  
  
## <a name="remarks"></a>Comentários  
 As matrizes `classIds` e `cObjects` são matrizes paralelas. Por exemplo, `classIds[i]` e `cObjects[i]` referenciam a mesma classe. Se nenhuma instância de uma classe tiver sido criada desde a coleta de lixo anterior, a classe será omitida. O retorno de chamada `ObjectsAllocatedByClass` não relatará objetos alocados na heap de objeto grande.  
  
 Os números relatados por `ObjectsAllocatedByClass` são apenas estimativas. Para contagens exatas, use [ICorProfilerCallback:: ObjectAllocated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md).  
  
 A matriz de `classIds` pode conter uma ou mais entradas nulas se a matriz de `cObjects` correspondente tiver tipos que estão descarregando.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
