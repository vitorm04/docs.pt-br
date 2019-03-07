---
title: Método ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.SetEnterLeaveFunctionHooks3WithInfo Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo
helpviewer_keywords:
- SetEnterLeaveFunctionHooks3WithInfo method [.NET Framework profiling]
- ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method [.NET Framework profiling]
ms.assetid: ca8ea534-e441-47b8-be85-466410988c0a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 287f08c4ce5108ac9ae871135976cb45917fa861
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57476694"
---
# <a name="icorprofilerinfo3setenterleavefunctionhooks3withinfo-method"></a><span data-ttu-id="45c88-102">Método ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="45c88-102">ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo Method</span></span>
<span data-ttu-id="45c88-103">Especifica as funções implementadas pelo criador de perfil que serão chamadas na [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), e [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) ganchos de funções gerenciadas.</span><span class="sxs-lookup"><span data-stu-id="45c88-103">Specifies the profiler-implemented functions that will be called on the [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) hooks of managed functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45c88-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="45c88-104">Syntax</span></span>  
  
```  
HRESULT SetEnterLeaveFunctionHooks3WithInfo(  
            [in] FunctionEnter3WithInfo    *pFuncEnter3,  
            [in] FunctionLeave3withInfo    *pFuncLeave3,  
            [in] FunctionTailcall3WithInfo *pFuncTailcall3);  
```  
  
## <a name="parameters"></a><span data-ttu-id="45c88-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="45c88-105">Parameters</span></span>  
 `pFuncEnter3`  
 <span data-ttu-id="45c88-106">[in] Um ponteiro para a implementação a ser usado como o `FunctionEnter3WithInfo` retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="45c88-106">[in] A pointer to the implementation to be used as the `FunctionEnter3WithInfo` callback.</span></span>  
  
 `pFuncLeave3`  
 <span data-ttu-id="45c88-107">[in] Um ponteiro para a implementação a ser usado como o `FunctionLeave3WithInfo` retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="45c88-107">[in] A pointer to the implementation to be used as the `FunctionLeave3WithInfo` callback.</span></span>  
  
 `pFuncTailcall3`  
 <span data-ttu-id="45c88-108">[in] Um ponteiro para a implementação a ser usado como o `FunctionTailcall3WithInfo` retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="45c88-108">[in] A pointer to the implementation to be used as the `FunctionTailcall3WithInfo` callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="45c88-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="45c88-109">Remarks</span></span>  
 <span data-ttu-id="45c88-110">O [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), e [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) ganchos fornecem inspeção de quadro e o argumento de pilha.</span><span class="sxs-lookup"><span data-stu-id="45c88-110">The [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) hooks provide stack frame and argument inspection.</span></span> <span data-ttu-id="45c88-111">Para acessar essas informações, o `COR_PRF_ENABLE_FUNCTION_ARGS`, `COR_PRF_ENABLE_FUNCTION_RETVAL`, e/ou `COR_PRF_ENABLE_FRAME_INFO` sinalizadores precisam ser configuradas.</span><span class="sxs-lookup"><span data-stu-id="45c88-111">To access that information, the `COR_PRF_ENABLE_FUNCTION_ARGS`, `COR_PRF_ENABLE_FUNCTION_RETVAL`, and/or `COR_PRF_ENABLE_FRAME_INFO` flags have to be set.</span></span> <span data-ttu-id="45c88-112">O criador de perfil pode usar o [ICorProfilerInfo:: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) método para definir os sinalizadores de evento e, em seguida, use o `SetEnterLeaveFunctionHooks3WithInfo` método para registrar sua implementação dessa função.</span><span class="sxs-lookup"><span data-stu-id="45c88-112">The profiler can use the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the event flags, and then use the `SetEnterLeaveFunctionHooks3WithInfo` method to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="45c88-113">Apenas um conjunto de retornos de chamada pode estar ativo por vez, e a versão mais recente tem precedência.</span><span class="sxs-lookup"><span data-stu-id="45c88-113">Only one set of callbacks may be active at a time, and the newest version takes precedence.</span></span> <span data-ttu-id="45c88-114">Portanto, se um criador de perfil chama ambos [SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md) e `SetEnterLeaveFunctionHooks3WithInfo`, `SetEnterLeaveFunctionHooks3WithInfo` é usado.</span><span class="sxs-lookup"><span data-stu-id="45c88-114">Therefore, if a profiler calls both [SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md) and `SetEnterLeaveFunctionHooks3WithInfo`, `SetEnterLeaveFunctionHooks3WithInfo` is used.</span></span>  
  
 <span data-ttu-id="45c88-115">O `SetEnterLeaveFunctionHooks3WithInfo` método pode ser chamado apenas do criador de perfil [ICorProfilerCallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="45c88-115">The `SetEnterLeaveFunctionHooks3WithInfo` method may be called only from the profiler's [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45c88-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="45c88-116">Requirements</span></span>  
 <span data-ttu-id="45c88-117">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45c88-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45c88-118">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="45c88-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="45c88-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="45c88-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="45c88-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45c88-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45c88-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="45c88-121">See also</span></span>
- [<span data-ttu-id="45c88-122">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="45c88-122">SetEnterLeaveFunctionHooks3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="45c88-123">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="45c88-123">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)
- [<span data-ttu-id="45c88-124">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="45c88-124">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)
- [<span data-ttu-id="45c88-125">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="45c88-125">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [<span data-ttu-id="45c88-126">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="45c88-126">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [<span data-ttu-id="45c88-127">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="45c88-127">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [<span data-ttu-id="45c88-128">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="45c88-128">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [<span data-ttu-id="45c88-129">Criando perfil de funções estáticas globais</span><span class="sxs-lookup"><span data-stu-id="45c88-129">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
- [<span data-ttu-id="45c88-130">Interface ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="45c88-130">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="45c88-131">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="45c88-131">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="45c88-132">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="45c88-132">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
