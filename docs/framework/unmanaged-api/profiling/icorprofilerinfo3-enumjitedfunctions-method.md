---
title: Método ICorProfilerInfo3::EnumJITedFunctions
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.EnumJITedFunctions Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::EnumJITedFunctions
helpviewer_keywords:
- ICorProfilerInfo3::EnumJITedFunctions method [.NET Framework profiling]
- EnumJITedFunctions method [.NET Framework profiling]
ms.assetid: e2847a36-f460-45e2-9b6c-b33b008f40d9
topic_type:
- apiref
ms.openlocfilehash: d21a793a88cd7561da9acb7daab2dc3bfecf0fc7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449766"
---
# <a name="icorprofilerinfo3enumjitedfunctions-method"></a><span data-ttu-id="17662-102">Método ICorProfilerInfo3::EnumJITedFunctions</span><span class="sxs-lookup"><span data-stu-id="17662-102">ICorProfilerInfo3::EnumJITedFunctions Method</span></span>
<span data-ttu-id="17662-103">Returns an enumerator for all functions that were previously JIT-compiled.</span><span class="sxs-lookup"><span data-stu-id="17662-103">Returns an enumerator for all functions that were previously JIT-compiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17662-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="17662-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumJITedFunctions([out] ICorProfilerFunctionEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="17662-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="17662-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="17662-106">[out] A pointer to the [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) enumerator.</span><span class="sxs-lookup"><span data-stu-id="17662-106">[out] A pointer to the [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) enumerator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="17662-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="17662-107">Remarks</span></span>  
 <span data-ttu-id="17662-108">This method may overlap with `JITCompilation` callbacks such as the [ICorProfilerCallback::JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) method.</span><span class="sxs-lookup"><span data-stu-id="17662-108">This method may overlap with `JITCompilation` callbacks such as the [ICorProfilerCallback::JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) method.</span></span> <span data-ttu-id="17662-109">The enumerator returned by this method does not include functions that are loaded from native images generated with Ngen.exe.</span><span class="sxs-lookup"><span data-stu-id="17662-109">The enumerator returned by this method does not include functions that are loaded from native images generated with Ngen.exe.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="17662-110">The returned enumeration includes only "0" for the value of the `COR_PRF_FUNCTION::reJitId` field.</span><span class="sxs-lookup"><span data-stu-id="17662-110">The returned enumeration includes only "0" for the value of the `COR_PRF_FUNCTION::reJitId` field.</span></span>  <span data-ttu-id="17662-111">If you require valid `COR_PRF_FUNCTION::reJitId` values, use the [ICorProfilerInfo4::EnumJITedFunctions2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md) method.</span><span class="sxs-lookup"><span data-stu-id="17662-111">If you require valid `COR_PRF_FUNCTION::reJitId` values, use the [ICorProfilerInfo4::EnumJITedFunctions2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17662-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="17662-112">Requirements</span></span>  
 <span data-ttu-id="17662-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17662-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17662-114">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="17662-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="17662-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="17662-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="17662-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17662-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17662-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="17662-117">See also</span></span>

- [<span data-ttu-id="17662-118">Interface ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="17662-118">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="17662-119">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="17662-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="17662-120">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="17662-120">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
