---
title: Método ICorProfilerCallback2::RootReferences2
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.RootReferences2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::RootReferences2
helpviewer_keywords:
- RootReferences2 method [.NET Framework profiling]
- ICorProfilerCallback2::RootReferences2 method [.NET Framework profiling]
ms.assetid: 55a2f907-d216-42eb-8f2f-e5d59c2eebd6
topic_type:
- apiref
ms.openlocfilehash: dffd4365669da61f7b321110ad663c131ce591e6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439674"
---
# <a name="icorprofilercallback2rootreferences2-method"></a><span data-ttu-id="a7ccf-102">Método ICorProfilerCallback2::RootReferences2</span><span class="sxs-lookup"><span data-stu-id="a7ccf-102">ICorProfilerCallback2::RootReferences2 Method</span></span>
<span data-ttu-id="a7ccf-103">Notifies the profiler about root references after a garbage collection has occurred.</span><span class="sxs-lookup"><span data-stu-id="a7ccf-103">Notifies the profiler about root references after a garbage collection has occurred.</span></span> <span data-ttu-id="a7ccf-104">This method is an extension of the [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) method.</span><span class="sxs-lookup"><span data-stu-id="a7ccf-104">This method is an extension of the [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7ccf-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a7ccf-105">Syntax</span></span>  
  
```cpp  
HRESULT RootReferences2(  
    [in] ULONG  cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[],  
    [in, size_is(cRootRefs)] COR_PRF_GC_ROOT_KIND rootKinds[],  
    [in, size_is(cRootRefs)] COR_PRF_GC_ROOT_FLAGS rootFlags[],  
    [in, size_is(cRootRefs)] UINT_PTR rootIds[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a7ccf-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a7ccf-106">Parameters</span></span>  
 `cRootRefs`  
 <span data-ttu-id="a7ccf-107">[in] The number of elements in the `rootRefIds`, `rootKinds`, `rootFlags`, and `rootIds` arrays.</span><span class="sxs-lookup"><span data-stu-id="a7ccf-107">[in] The number of elements in the `rootRefIds`, `rootKinds`, `rootFlags`, and `rootIds` arrays.</span></span>  
  
 `rootRefIds`  
 <span data-ttu-id="a7ccf-108">[in] An array of object IDs, each of which references either a static object or an object on the stack.</span><span class="sxs-lookup"><span data-stu-id="a7ccf-108">[in] An array of object IDs, each of which references either a static object or an object on the stack.</span></span> <span data-ttu-id="a7ccf-109">Elements in the `rootKinds` array provide information to classify corresponding elements in the `rootRefIds` array.</span><span class="sxs-lookup"><span data-stu-id="a7ccf-109">Elements in the `rootKinds` array provide information to classify corresponding elements in the `rootRefIds` array.</span></span>  
  
 `rootKinds`  
 <span data-ttu-id="a7ccf-110">[in] An array of [COR_PRF_GC_ROOT_KIND](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-kind-enumeration.md) values that indicate the type of the garbage collection root.</span><span class="sxs-lookup"><span data-stu-id="a7ccf-110">[in] An array of [COR_PRF_GC_ROOT_KIND](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-kind-enumeration.md) values that indicate the type of the garbage collection root.</span></span>  
  
 `rootFlags`  
 <span data-ttu-id="a7ccf-111">[in] An array of [COR_PRF_GC_ROOT_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-flags-enumeration.md) values that describe the properties of a garbage collection root.</span><span class="sxs-lookup"><span data-stu-id="a7ccf-111">[in] An array of [COR_PRF_GC_ROOT_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-flags-enumeration.md) values that describe the properties of a garbage collection root.</span></span>  
  
 `rootIds`  
 <span data-ttu-id="a7ccf-112">[in] An array of UINT_PTR values that point to an integer that contains additional information about the garbage collection root, depending on the value of the `rootKinds` parameter.</span><span class="sxs-lookup"><span data-stu-id="a7ccf-112">[in] An array of UINT_PTR values that point to an integer that contains additional information about the garbage collection root, depending on the value of the `rootKinds` parameter.</span></span>  
  
 <span data-ttu-id="a7ccf-113">If the type of the root is a stack, the root ID is for the function that contains the variable.</span><span class="sxs-lookup"><span data-stu-id="a7ccf-113">If the type of the root is a stack, the root ID is for the function that contains the variable.</span></span> <span data-ttu-id="a7ccf-114">If that root ID is 0, the function is an unnamed function that is internal to the CLR.</span><span class="sxs-lookup"><span data-stu-id="a7ccf-114">If that root ID is 0, the function is an unnamed function that is internal to the CLR.</span></span> <span data-ttu-id="a7ccf-115">If the type of the root is a handle, the root ID is for the garbage collection handle.</span><span class="sxs-lookup"><span data-stu-id="a7ccf-115">If the type of the root is a handle, the root ID is for the garbage collection handle.</span></span> <span data-ttu-id="a7ccf-116">For the other root types, the ID is an opaque value and should be ignored.</span><span class="sxs-lookup"><span data-stu-id="a7ccf-116">For the other root types, the ID is an opaque value and should be ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a7ccf-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="a7ccf-117">Remarks</span></span>  
 <span data-ttu-id="a7ccf-118">The `rootRefIds`, `rootKinds`, `rootFlags`, and `rootIds` arrays are parallel arrays.</span><span class="sxs-lookup"><span data-stu-id="a7ccf-118">The `rootRefIds`, `rootKinds`, `rootFlags`, and `rootIds` arrays are parallel arrays.</span></span> <span data-ttu-id="a7ccf-119">That is, `rootRefIds[i]`, `rootKinds[i]`, `rootFlags[i]`, and `rootIds[i]` all concern the same root.</span><span class="sxs-lookup"><span data-stu-id="a7ccf-119">That is, `rootRefIds[i]`, `rootKinds[i]`, `rootFlags[i]`, and `rootIds[i]` all concern the same root.</span></span>  
  
 <span data-ttu-id="a7ccf-120">Both `RootReferences` and `RootReferences2` are called to notify the profiler.</span><span class="sxs-lookup"><span data-stu-id="a7ccf-120">Both `RootReferences` and `RootReferences2` are called to notify the profiler.</span></span> <span data-ttu-id="a7ccf-121">Profilers will normally implement one method or the other, but not both, because the information passed in `RootReferences2` is a superset of that passed in `RootReferences`.</span><span class="sxs-lookup"><span data-stu-id="a7ccf-121">Profilers will normally implement one method or the other, but not both, because the information passed in `RootReferences2` is a superset of that passed in `RootReferences`.</span></span>  
  
 <span data-ttu-id="a7ccf-122">It is possible for entries in `rootRefIds` to be zero, which implies that the corresponding root reference is null and does not refer to an object on the managed heap.</span><span class="sxs-lookup"><span data-stu-id="a7ccf-122">It is possible for entries in `rootRefIds` to be zero, which implies that the corresponding root reference is null and does not refer to an object on the managed heap.</span></span>  
  
 <span data-ttu-id="a7ccf-123">The object IDs returned by `RootReferences2` are not valid during the callback itself, because the garbage collection might be in the middle of moving objects from old addresses to new addresses.</span><span class="sxs-lookup"><span data-stu-id="a7ccf-123">The object IDs returned by `RootReferences2` are not valid during the callback itself, because the garbage collection might be in the middle of moving objects from old addresses to new addresses.</span></span> <span data-ttu-id="a7ccf-124">Portanto, os criadores de perfis não devem tentar inspecionar objetos durante uma chamada `RootReferences2`.</span><span class="sxs-lookup"><span data-stu-id="a7ccf-124">Therefore, profilers should not attempt to inspect objects during a `RootReferences2` call.</span></span> <span data-ttu-id="a7ccf-125">When [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) is called, all objects have been moved to their new locations and can be safely inspected.</span><span class="sxs-lookup"><span data-stu-id="a7ccf-125">When [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) is called, all objects have been moved to their new locations and can be safely inspected.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7ccf-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a7ccf-126">Requirements</span></span>  
 <span data-ttu-id="a7ccf-127">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7ccf-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7ccf-128">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a7ccf-128">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a7ccf-129">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a7ccf-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a7ccf-130">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7ccf-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7ccf-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a7ccf-131">See also</span></span>

- [<span data-ttu-id="a7ccf-132">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="a7ccf-132">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="a7ccf-133">Interface ICorProfilerCallback2</span><span class="sxs-lookup"><span data-stu-id="a7ccf-133">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
