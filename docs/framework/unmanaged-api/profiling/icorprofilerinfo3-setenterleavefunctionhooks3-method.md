---
title: "Método ICorProfilerInfo3::SetEnterLeaveFunctionHooks3"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo3.SetEnterLeaveFunctionHooks3 Method
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo3::SetEnterLeaveFunctionHooks3
helpviewer_keywords:
- SetEnterLeaveFunctionHooks3 method [.NET Framework profiling]
- ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method [.NET Framework profiling]
ms.assetid: f0621465-b84f-40ab-a4e5-56a7abc776a7
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f36a73d26bae96a57d205bb85fa232d16a964dc5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo3setenterleavefunctionhooks3-method"></a><span data-ttu-id="10f3e-102">Método ICorProfilerInfo3::SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="10f3e-102">ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 Method</span></span>
<span data-ttu-id="10f3e-103">Especifica as funções implementada pelo criador de perfil que serão chamadas no [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), e [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md) funções.</span><span class="sxs-lookup"><span data-stu-id="10f3e-103">Specifies the profiler-implemented functions that will be called on the [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), and [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md) functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10f3e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="10f3e-104">Syntax</span></span>  
  
```  
HRESULT SetEnterLeaveFunctionHooks3(  
            [in] FunctionEnter3    *pFuncEnter3,  
            [in] FunctionLeave3    *pFuncLeave3,  
            [in] FunctionTailcall3 *pFuncTailcall3);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="10f3e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="10f3e-105">Parameters</span></span>  
 `pFuncEnter3`  
 <span data-ttu-id="10f3e-106">[in] Um ponteiro para a implementação para ser usado como o `FunctionEnter3` retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="10f3e-106">[in] A pointer to the implementation to be used as the `FunctionEnter3` callback.</span></span>  
  
 `pFuncLeave3`  
 <span data-ttu-id="10f3e-107">[in] Um ponteiro para a implementação para ser usado como o `FunctionLeave3` retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="10f3e-107">[in] A pointer to the implementation to be used as the `FunctionLeave3` callback.</span></span>  
  
 `pFuncTailcall3`  
 <span data-ttu-id="10f3e-108">[in] Um ponteiro para a implementação para ser usado como o `FunctionTailcall3` retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="10f3e-108">[in] A pointer to the implementation to be used as the `FunctionTailcall3` callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="10f3e-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="10f3e-109">Remarks</span></span>  
 <span data-ttu-id="10f3e-110">[FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), e [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md) ganchos não fornecem a inspeção de argumento e de quadro de pilha.</span><span class="sxs-lookup"><span data-stu-id="10f3e-110">[FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), and [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md) hooks do not provide stack frame and argument inspection.</span></span> <span data-ttu-id="10f3e-111">Para acessar essas informações, o `COR_PRF_ENABLE_FUNCTION_ARGS`, `COR_PRF_ENABLE_FUNCTION_RETVAL`, e/ou `COR_PRF_ENABLE_FRAME_INFO` sinalizadores precisam ser definido.</span><span class="sxs-lookup"><span data-stu-id="10f3e-111">To access that information, the `COR_PRF_ENABLE_FUNCTION_ARGS`, `COR_PRF_ENABLE_FUNCTION_RETVAL`, and/or  `COR_PRF_ENABLE_FRAME_INFO` flags have to be set.</span></span> <span data-ttu-id="10f3e-112">O criador de perfil pode usar o [: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) método para definir os sinalizadores de evento e, em seguida, use o [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) método para registrar seu implementação dessa função.</span><span class="sxs-lookup"><span data-stu-id="10f3e-112">The profiler can use the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) method to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="10f3e-113">Apenas um conjunto de retornos de chamada pode estar ativo por vez, e a versão mais recente tem precedência.</span><span class="sxs-lookup"><span data-stu-id="10f3e-113">Only one set of callbacks may be active at a time, and the newest version takes precedence.</span></span> <span data-ttu-id="10f3e-114">Portanto, se um criador de perfil chama ambos o [método SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md) e o `SetEnterLeaveFunctionHooks3` método `SetEnterLeaveFunctionHooks3` é usado.</span><span class="sxs-lookup"><span data-stu-id="10f3e-114">Therefore, if a profiler calls both the [SetEnterLeaveFunctionHooks2 Method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md) and the `SetEnterLeaveFunctionHooks3` method, `SetEnterLeaveFunctionHooks3` is used.</span></span>  
  
 <span data-ttu-id="10f3e-115">O `SetEnterLeaveFunctionHooks3` método pode ser chamado somente a partir do criador de perfil [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="10f3e-115">The `SetEnterLeaveFunctionHooks3` method may be called only from the profiler's [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10f3e-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="10f3e-116">Requirements</span></span>  
 <span data-ttu-id="10f3e-117">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="10f3e-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10f3e-118">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="10f3e-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="10f3e-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="10f3e-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="10f3e-120">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10f3e-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10f3e-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="10f3e-121">See Also</span></span>  
 [<span data-ttu-id="10f3e-122">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="10f3e-122">SetEnterLeaveFunctionHooks3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)  
 [<span data-ttu-id="10f3e-123">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="10f3e-123">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)  
 [<span data-ttu-id="10f3e-124">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="10f3e-124">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)  
 [<span data-ttu-id="10f3e-125">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="10f3e-125">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)  
 [<span data-ttu-id="10f3e-126">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="10f3e-126">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)  
 [<span data-ttu-id="10f3e-127">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="10f3e-127">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 [<span data-ttu-id="10f3e-128">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="10f3e-128">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 [<span data-ttu-id="10f3e-129">Funções estáticas globais de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="10f3e-129">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
 [<span data-ttu-id="10f3e-130">ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="10f3e-130">ICorProfilerInfo3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="10f3e-131">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="10f3e-131">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="10f3e-132">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="10f3e-132">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
