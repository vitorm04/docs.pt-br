---
title: Método ICorProfilerCallback::AssemblyUnloadFinished
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyUnloadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyUnloadFinished
helpviewer_keywords:
- AssemblyUnloadFinished method [.NET Framework profiling]
- ICorProfilerCallback::AssemblyUnloadFinished method [.NET Framework profiling]
ms.assetid: 53fca564-84b1-44d4-9e21-17a492d2aae7
topic_type:
- apiref
ms.openlocfilehash: 01404d23707be90b6b15cf741632400d49f164de
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445142"
---
# <a name="icorprofilercallbackassemblyunloadfinished-method"></a><span data-ttu-id="aca8f-102">Método ICorProfilerCallback::AssemblyUnloadFinished</span><span class="sxs-lookup"><span data-stu-id="aca8f-102">ICorProfilerCallback::AssemblyUnloadFinished Method</span></span>
<span data-ttu-id="aca8f-103">Notifies the profiler that an assembly has been unloaded.</span><span class="sxs-lookup"><span data-stu-id="aca8f-103">Notifies the profiler that an assembly has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aca8f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="aca8f-104">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyUnloadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aca8f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="aca8f-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="aca8f-106">[in] Identifies the assembly that is being unloaded.</span><span class="sxs-lookup"><span data-stu-id="aca8f-106">[in] Identifies the assembly that is being unloaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="aca8f-107">[in] An HRESULT that indicates whether the assembly was unloaded successfully.</span><span class="sxs-lookup"><span data-stu-id="aca8f-107">[in] An HRESULT that indicates whether the assembly was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aca8f-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="aca8f-108">Remarks</span></span>  
 <span data-ttu-id="aca8f-109">The value of `assemblyId` is not valid for an information request after the [ICorProfilerCallback::AssemblyUnloadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadstarted-method.md) method returns.</span><span class="sxs-lookup"><span data-stu-id="aca8f-109">The value of `assemblyId` is not valid for an information request after the [ICorProfilerCallback::AssemblyUnloadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="aca8f-110">Some parts of unloading the assembly might continue after the `AssemblyUnloadFinished` callback.</span><span class="sxs-lookup"><span data-stu-id="aca8f-110">Some parts of unloading the assembly might continue after the `AssemblyUnloadFinished` callback.</span></span> <span data-ttu-id="aca8f-111">A failure HRESULT in `hrStatus` indicates a failure.</span><span class="sxs-lookup"><span data-stu-id="aca8f-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="aca8f-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the assembly has succeeded.</span><span class="sxs-lookup"><span data-stu-id="aca8f-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the assembly has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aca8f-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="aca8f-113">Requirements</span></span>  
 <span data-ttu-id="aca8f-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aca8f-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aca8f-115">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="aca8f-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="aca8f-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aca8f-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aca8f-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aca8f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aca8f-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aca8f-118">See also</span></span>

- [<span data-ttu-id="aca8f-119">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="aca8f-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
