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
ms.openlocfilehash: 4229332ef3a079a5a294e27b624dde0e1fb46691
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782958"
---
# <a name="icorprofilercallbackobjectsallocatedbyclass-method"></a><span data-ttu-id="a1b39-102">Método ICorProfilerCallback::ObjectsAllocatedByClass</span><span class="sxs-lookup"><span data-stu-id="a1b39-102">ICorProfilerCallback::ObjectsAllocatedByClass Method</span></span>
<span data-ttu-id="a1b39-103">Notifica o criador de perfil sobre o número de instâncias de cada classe especificada que foram criados desde a última coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="a1b39-103">Notifies the profiler about the number of instances of each specified class that have been created since the most recent garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1b39-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a1b39-104">Syntax</span></span>  
  
```cpp  
HRESULT ObjectsAllocatedByClass(  
    [in] ULONG   cClassCount,  
    [in, size_is(cClassCount)] ClassID classIds[] ,  
    [in, size_is(cClassCount)] ULONG   cObjects[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="a1b39-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a1b39-105">Parameters</span></span>  
 `cClassCount`  
 <span data-ttu-id="a1b39-106">[in] O tamanho do `classIds` e `cObjects` matrizes.</span><span class="sxs-lookup"><span data-stu-id="a1b39-106">[in] The size of the `classIds` and `cObjects` arrays.</span></span>  
  
 `classIds`  
 <span data-ttu-id="a1b39-107">[in] Uma matriz de IDs, onde cada ID Especifica uma classe com uma ou mais instâncias de classe.</span><span class="sxs-lookup"><span data-stu-id="a1b39-107">[in] An array of class IDs, where each ID specifies a class with one or more instances.</span></span>  
  
 `cObjects`  
 <span data-ttu-id="a1b39-108">[in] Uma matriz de inteiros, onde cada inteiro Especifica o número de instâncias da classe correspondente no `classIds` matriz.</span><span class="sxs-lookup"><span data-stu-id="a1b39-108">[in] An array of integers, where each integer specifies the number of instances for the corresponding class in the `classIds` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a1b39-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="a1b39-109">Remarks</span></span>  
 <span data-ttu-id="a1b39-110">O `classIds` e `cObjects` matrizes são matrizes paralelas.</span><span class="sxs-lookup"><span data-stu-id="a1b39-110">The `classIds` and `cObjects` arrays are parallel arrays.</span></span> <span data-ttu-id="a1b39-111">Por exemplo, `classIds[i]` e `cObjects[i]` fazer referência à mesma classe.</span><span class="sxs-lookup"><span data-stu-id="a1b39-111">For example, `classIds[i]` and `cObjects[i]` reference the same class.</span></span> <span data-ttu-id="a1b39-112">Se nenhuma instância de uma classe tiver sido criada desde a coleta de lixo anterior, a classe é omitida.</span><span class="sxs-lookup"><span data-stu-id="a1b39-112">If no instance of a class has been created since the previous garbage collection, the class is omitted.</span></span> <span data-ttu-id="a1b39-113">O `ObjectsAllocatedByClass` retorno de chamada não relatará objetos alocados no heap de objeto grande.</span><span class="sxs-lookup"><span data-stu-id="a1b39-113">The `ObjectsAllocatedByClass` callback will not report objects allocated in the large object heap.</span></span>  
  
 <span data-ttu-id="a1b39-114">Os números relatados pelo `ObjectsAllocatedByClass` são apenas estimativas.</span><span class="sxs-lookup"><span data-stu-id="a1b39-114">The numbers reported by `ObjectsAllocatedByClass` are only estimates.</span></span> <span data-ttu-id="a1b39-115">Para a contagem exata, use [ICorProfilerCallback:: ObjectAllocated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md).</span><span class="sxs-lookup"><span data-stu-id="a1b39-115">For exact counts, use [ICorProfilerCallback::ObjectAllocated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md).</span></span>  
  
 <span data-ttu-id="a1b39-116">O `classIds` matriz pode conter um ou mais entradas nulas se correspondente `cObjects` matriz tem tipos estão descarregando.</span><span class="sxs-lookup"><span data-stu-id="a1b39-116">The `classIds` array may contain one or more null entries if the corresponding `cObjects` array has types that are unloading.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1b39-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a1b39-117">Requirements</span></span>  
 <span data-ttu-id="a1b39-118">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1b39-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1b39-119">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a1b39-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a1b39-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a1b39-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a1b39-121">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1b39-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1b39-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a1b39-122">See also</span></span>

- [<span data-ttu-id="a1b39-123">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="a1b39-123">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
