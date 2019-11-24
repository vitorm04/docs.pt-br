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
# <a name="icorprofilercallbackobjectsallocatedbyclass-method"></a><span data-ttu-id="0b43a-102">Método ICorProfilerCallback::ObjectsAllocatedByClass</span><span class="sxs-lookup"><span data-stu-id="0b43a-102">ICorProfilerCallback::ObjectsAllocatedByClass Method</span></span>
<span data-ttu-id="0b43a-103">Notifica o criador de perfil sobre o número de instâncias de cada classe especificada que foram criadas desde a coleta de lixo mais recente.</span><span class="sxs-lookup"><span data-stu-id="0b43a-103">Notifies the profiler about the number of instances of each specified class that have been created since the most recent garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b43a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0b43a-104">Syntax</span></span>  
  
```cpp  
HRESULT ObjectsAllocatedByClass(  
    [in] ULONG   cClassCount,  
    [in, size_is(cClassCount)] ClassID classIds[] ,  
    [in, size_is(cClassCount)] ULONG   cObjects[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="0b43a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0b43a-105">Parameters</span></span>  
 `cClassCount`  
 <span data-ttu-id="0b43a-106">no O tamanho das matrizes `classIds` e `cObjects`.</span><span class="sxs-lookup"><span data-stu-id="0b43a-106">[in] The size of the `classIds` and `cObjects` arrays.</span></span>  
  
 `classIds`  
 <span data-ttu-id="0b43a-107">no Uma matriz de IDs de classe, em que cada ID especifica uma classe com uma ou mais instâncias.</span><span class="sxs-lookup"><span data-stu-id="0b43a-107">[in] An array of class IDs, where each ID specifies a class with one or more instances.</span></span>  
  
 `cObjects`  
 <span data-ttu-id="0b43a-108">no Uma matriz de inteiros, em que cada inteiro especifica o número de instâncias para a classe correspondente na matriz de `classIds`.</span><span class="sxs-lookup"><span data-stu-id="0b43a-108">[in] An array of integers, where each integer specifies the number of instances for the corresponding class in the `classIds` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0b43a-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="0b43a-109">Remarks</span></span>  
 <span data-ttu-id="0b43a-110">As matrizes `classIds` e `cObjects` são matrizes paralelas.</span><span class="sxs-lookup"><span data-stu-id="0b43a-110">The `classIds` and `cObjects` arrays are parallel arrays.</span></span> <span data-ttu-id="0b43a-111">Por exemplo, `classIds[i]` e `cObjects[i]` referenciam a mesma classe.</span><span class="sxs-lookup"><span data-stu-id="0b43a-111">For example, `classIds[i]` and `cObjects[i]` reference the same class.</span></span> <span data-ttu-id="0b43a-112">Se nenhuma instância de uma classe tiver sido criada desde a coleta de lixo anterior, a classe será omitida.</span><span class="sxs-lookup"><span data-stu-id="0b43a-112">If no instance of a class has been created since the previous garbage collection, the class is omitted.</span></span> <span data-ttu-id="0b43a-113">O retorno de chamada `ObjectsAllocatedByClass` não relatará objetos alocados na heap de objeto grande.</span><span class="sxs-lookup"><span data-stu-id="0b43a-113">The `ObjectsAllocatedByClass` callback will not report objects allocated in the large object heap.</span></span>  
  
 <span data-ttu-id="0b43a-114">Os números relatados por `ObjectsAllocatedByClass` são apenas estimativas.</span><span class="sxs-lookup"><span data-stu-id="0b43a-114">The numbers reported by `ObjectsAllocatedByClass` are only estimates.</span></span> <span data-ttu-id="0b43a-115">Para contagens exatas, use [ICorProfilerCallback:: ObjectAllocated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md).</span><span class="sxs-lookup"><span data-stu-id="0b43a-115">For exact counts, use [ICorProfilerCallback::ObjectAllocated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md).</span></span>  
  
 <span data-ttu-id="0b43a-116">A matriz de `classIds` pode conter uma ou mais entradas nulas se a matriz de `cObjects` correspondente tiver tipos que estão descarregando.</span><span class="sxs-lookup"><span data-stu-id="0b43a-116">The `classIds` array may contain one or more null entries if the corresponding `cObjects` array has types that are unloading.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b43a-117">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="0b43a-117">Requirements</span></span>  
 <span data-ttu-id="0b43a-118">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b43a-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b43a-119">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="0b43a-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0b43a-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0b43a-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0b43a-121">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b43a-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b43a-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0b43a-122">See also</span></span>

- [<span data-ttu-id="0b43a-123">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="0b43a-123">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
