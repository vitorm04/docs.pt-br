---
title: Método ICorProfilerInfo3::SetEnterLeaveFunctionHooks3
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.SetEnterLeaveFunctionHooks3 Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::SetEnterLeaveFunctionHooks3
helpviewer_keywords:
- SetEnterLeaveFunctionHooks3 method [.NET Framework profiling]
- ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method [.NET Framework profiling]
ms.assetid: f0621465-b84f-40ab-a4e5-56a7abc776a7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d72b336f9d71d0b7b7252ba907e8eebd3b42c200
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57473156"
---
# <a name="icorprofilerinfo3setenterleavefunctionhooks3-method"></a><span data-ttu-id="d692f-102">Método ICorProfilerInfo3::SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="d692f-102">ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 Method</span></span>
<span data-ttu-id="d692f-103">Especifica as funções implementadas pelo criador de perfil que serão chamadas na [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), e [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md) funções.</span><span class="sxs-lookup"><span data-stu-id="d692f-103">Specifies the profiler-implemented functions that will be called on the [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), and [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md) functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d692f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d692f-104">Syntax</span></span>  
  
```  
HRESULT SetEnterLeaveFunctionHooks3(  
            [in] FunctionEnter3    *pFuncEnter3,  
            [in] FunctionLeave3    *pFuncLeave3,  
            [in] FunctionTailcall3 *pFuncTailcall3);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d692f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d692f-105">Parameters</span></span>  
 `pFuncEnter3`  
 <span data-ttu-id="d692f-106">[in] Um ponteiro para a implementação a ser usado como o `FunctionEnter3` retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="d692f-106">[in] A pointer to the implementation to be used as the `FunctionEnter3` callback.</span></span>  
  
 `pFuncLeave3`  
 <span data-ttu-id="d692f-107">[in] Um ponteiro para a implementação a ser usado como o `FunctionLeave3` retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="d692f-107">[in] A pointer to the implementation to be used as the `FunctionLeave3` callback.</span></span>  
  
 `pFuncTailcall3`  
 <span data-ttu-id="d692f-108">[in] Um ponteiro para a implementação a ser usado como o `FunctionTailcall3` retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="d692f-108">[in] A pointer to the implementation to be used as the `FunctionTailcall3` callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d692f-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="d692f-109">Remarks</span></span>  
 <span data-ttu-id="d692f-110">[FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), e [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md) ganchos não fornecem inspeção de quadro e o argumento de pilha.</span><span class="sxs-lookup"><span data-stu-id="d692f-110">[FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), and [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md) hooks do not provide stack frame and argument inspection.</span></span> <span data-ttu-id="d692f-111">Para acessar essas informações, o `COR_PRF_ENABLE_FUNCTION_ARGS`, `COR_PRF_ENABLE_FUNCTION_RETVAL`, e/ou `COR_PRF_ENABLE_FRAME_INFO` sinalizadores precisam ser configuradas.</span><span class="sxs-lookup"><span data-stu-id="d692f-111">To access that information, the `COR_PRF_ENABLE_FUNCTION_ARGS`, `COR_PRF_ENABLE_FUNCTION_RETVAL`, and/or  `COR_PRF_ENABLE_FRAME_INFO` flags have to be set.</span></span> <span data-ttu-id="d692f-112">O criador de perfil pode usar o [ICorProfilerInfo:: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) método para definir os sinalizadores de evento e, em seguida, usar o [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) método para registrar seu implementação dessa função.</span><span class="sxs-lookup"><span data-stu-id="d692f-112">The profiler can use the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) method to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="d692f-113">Apenas um conjunto de retornos de chamada pode estar ativo por vez, e a versão mais recente tem precedência.</span><span class="sxs-lookup"><span data-stu-id="d692f-113">Only one set of callbacks may be active at a time, and the newest version takes precedence.</span></span> <span data-ttu-id="d692f-114">Portanto, se um criador de perfil chama o [método SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md) e o `SetEnterLeaveFunctionHooks3` método, `SetEnterLeaveFunctionHooks3` é usado.</span><span class="sxs-lookup"><span data-stu-id="d692f-114">Therefore, if a profiler calls both the [SetEnterLeaveFunctionHooks2 Method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md) and the `SetEnterLeaveFunctionHooks3` method, `SetEnterLeaveFunctionHooks3` is used.</span></span>  
  
 <span data-ttu-id="d692f-115">O `SetEnterLeaveFunctionHooks3` método pode ser chamado apenas do criador de perfil [ICorProfilerCallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="d692f-115">The `SetEnterLeaveFunctionHooks3` method may be called only from the profiler's [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d692f-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d692f-116">Requirements</span></span>  
 <span data-ttu-id="d692f-117">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d692f-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d692f-118">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d692f-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d692f-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d692f-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d692f-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d692f-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d692f-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d692f-121">See also</span></span>
- [<span data-ttu-id="d692f-122">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="d692f-122">SetEnterLeaveFunctionHooks3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="d692f-123">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="d692f-123">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)
- [<span data-ttu-id="d692f-124">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="d692f-124">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)
- [<span data-ttu-id="d692f-125">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="d692f-125">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [<span data-ttu-id="d692f-126">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="d692f-126">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [<span data-ttu-id="d692f-127">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="d692f-127">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [<span data-ttu-id="d692f-128">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="d692f-128">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [<span data-ttu-id="d692f-129">Criando perfil de funções estáticas globais</span><span class="sxs-lookup"><span data-stu-id="d692f-129">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
- [<span data-ttu-id="d692f-130">ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="d692f-130">ICorProfilerInfo3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="d692f-131">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="d692f-131">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="d692f-132">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="d692f-132">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
