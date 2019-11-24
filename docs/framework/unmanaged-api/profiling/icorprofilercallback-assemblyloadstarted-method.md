---
title: Método ICorProfilerCallback::AssemblyLoadStarted
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyLoadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyLoadStarted
helpviewer_keywords:
- ICorProfilerCallback::AssemblyLoadStarted method [.NET Framework profiling]
- AssemblyLoadStarted method [.NET Framework profiling]
ms.assetid: 67e8209d-a0ca-4118-a6e6-c1ee0abc2221
topic_type:
- apiref
ms.openlocfilehash: 34744132442440ef160841db5a50bf75355f2410
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445166"
---
# <a name="icorprofilercallbackassemblyloadstarted-method"></a><span data-ttu-id="64f24-102">Método ICorProfilerCallback::AssemblyLoadStarted</span><span class="sxs-lookup"><span data-stu-id="64f24-102">ICorProfilerCallback::AssemblyLoadStarted Method</span></span>
<span data-ttu-id="64f24-103">Notifies the profiler that an assembly is being loaded.</span><span class="sxs-lookup"><span data-stu-id="64f24-103">Notifies the profiler that an assembly is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64f24-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="64f24-104">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyLoadStarted(  
    [in] AssemblyID assemblyId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="64f24-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="64f24-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="64f24-106">[in] Identifies the assembly that is being loaded.</span><span class="sxs-lookup"><span data-stu-id="64f24-106">[in] Identifies the assembly that is being loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="64f24-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="64f24-107">Remarks</span></span>  
 <span data-ttu-id="64f24-108">The value of `assemblyId` is not valid for an information request until the [ICorProfilerCallback::AssemblyLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyloadfinished-method.md) method is called.</span><span class="sxs-lookup"><span data-stu-id="64f24-108">The value of `assemblyId` is not valid for an information request until the [ICorProfilerCallback::AssemblyLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64f24-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="64f24-109">Requirements</span></span>  
 <span data-ttu-id="64f24-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64f24-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64f24-111">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="64f24-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="64f24-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="64f24-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="64f24-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64f24-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64f24-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="64f24-114">See also</span></span>

- [<span data-ttu-id="64f24-115">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="64f24-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
