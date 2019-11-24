---
title: Método ICorProfilerCallback::ModuleAttachedToAssembly
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleAttachedToAssembly
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleAttachedToAssembly
helpviewer_keywords:
- ICorProfilerCallback::ModuleAttachedToAssembly method [.NET Framework profiling]
- ModuleAttachedToAssembly method [.NET Framework profiling]
ms.assetid: b595798a-5d40-4cac-ab4f-911c61d2c5d2
topic_type:
- apiref
ms.openlocfilehash: d229b530062d759ab270612fa70b1799acbcadbe
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448074"
---
# <a name="icorprofilercallbackmoduleattachedtoassembly-method"></a><span data-ttu-id="abe84-102">Método ICorProfilerCallback::ModuleAttachedToAssembly</span><span class="sxs-lookup"><span data-stu-id="abe84-102">ICorProfilerCallback::ModuleAttachedToAssembly Method</span></span>
<span data-ttu-id="abe84-103">Notifies the profiler that a module is being attached to its parent assembly.</span><span class="sxs-lookup"><span data-stu-id="abe84-103">Notifies the profiler that a module is being attached to its parent assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abe84-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="abe84-104">Syntax</span></span>  
  
```cpp  
HRESULT ModuleAttachedToAssembly(  
    [in] ModuleID   moduleId,  
    [in] AssemblyID AssemblyId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="abe84-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="abe84-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="abe84-106">[in] The ID of the module that is being attached.</span><span class="sxs-lookup"><span data-stu-id="abe84-106">[in] The ID of the module that is being attached.</span></span>  
  
 `AssemblyId`  
 <span data-ttu-id="abe84-107">[in] The ID of the parent assembly to which the module is attached.</span><span class="sxs-lookup"><span data-stu-id="abe84-107">[in] The ID of the parent assembly to which the module is attached.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="abe84-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="abe84-108">Remarks</span></span>  
 <span data-ttu-id="abe84-109">A module can be loaded through an import address table (IAT), through a call to `LoadLibrary`, or through a metadata reference.</span><span class="sxs-lookup"><span data-stu-id="abe84-109">A module can be loaded through an import address table (IAT), through a call to `LoadLibrary`, or through a metadata reference.</span></span> <span data-ttu-id="abe84-110">As a result, the common language runtime (CLR) loader has multiple code paths for determining the assembly in which a module lives.</span><span class="sxs-lookup"><span data-stu-id="abe84-110">As a result, the common language runtime (CLR) loader has multiple code paths for determining the assembly in which a module lives.</span></span> <span data-ttu-id="abe84-111">Therefore, it is possible that after [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) is called, the module does not know what assembly it is in and getting the parent assembly ID is not possible.</span><span class="sxs-lookup"><span data-stu-id="abe84-111">Therefore, it is possible that after [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) is called, the module does not know what assembly it is in and getting the parent assembly ID is not possible.</span></span> <span data-ttu-id="abe84-112">The `ModuleAttachedToAssembly` method is called when the module is attached to its parent assembly and its parent assembly ID can be obtained.</span><span class="sxs-lookup"><span data-stu-id="abe84-112">The `ModuleAttachedToAssembly` method is called when the module is attached to its parent assembly and its parent assembly ID can be obtained.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="abe84-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="abe84-113">Requirements</span></span>  
 <span data-ttu-id="abe84-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="abe84-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="abe84-115">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="abe84-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="abe84-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="abe84-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="abe84-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="abe84-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abe84-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="abe84-118">See also</span></span>

- [<span data-ttu-id="abe84-119">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="abe84-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
