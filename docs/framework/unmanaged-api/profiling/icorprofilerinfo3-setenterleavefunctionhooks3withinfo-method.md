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
ms.openlocfilehash: b17ab9382e5195881e5629d482e4327fc67562f9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449597"
---
# <a name="icorprofilerinfo3setenterleavefunctionhooks3withinfo-method"></a><span data-ttu-id="cc520-102">Método ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="cc520-102">ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo Method</span></span>
<span data-ttu-id="cc520-103">Especifica as funções implementadas pelo criador de perfil que serão chamadas nos ganchos [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)e [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) das funções gerenciadas.</span><span class="sxs-lookup"><span data-stu-id="cc520-103">Specifies the profiler-implemented functions that will be called on the [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) hooks of managed functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc520-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cc520-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks3WithInfo(  
            [in] FunctionEnter3WithInfo    *pFuncEnter3,  
            [in] FunctionLeave3withInfo    *pFuncLeave3,  
            [in] FunctionTailcall3WithInfo *pFuncTailcall3);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cc520-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cc520-105">Parameters</span></span>  
 `pFuncEnter3`  
 <span data-ttu-id="cc520-106">no Um ponteiro para a implementação a ser usado como o retorno de chamada `FunctionEnter3WithInfo`.</span><span class="sxs-lookup"><span data-stu-id="cc520-106">[in] A pointer to the implementation to be used as the `FunctionEnter3WithInfo` callback.</span></span>  
  
 `pFuncLeave3`  
 <span data-ttu-id="cc520-107">no Um ponteiro para a implementação a ser usado como o retorno de chamada `FunctionLeave3WithInfo`.</span><span class="sxs-lookup"><span data-stu-id="cc520-107">[in] A pointer to the implementation to be used as the `FunctionLeave3WithInfo` callback.</span></span>  
  
 `pFuncTailcall3`  
 <span data-ttu-id="cc520-108">no Um ponteiro para a implementação a ser usado como o retorno de chamada `FunctionTailcall3WithInfo`.</span><span class="sxs-lookup"><span data-stu-id="cc520-108">[in] A pointer to the implementation to be used as the `FunctionTailcall3WithInfo` callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cc520-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="cc520-109">Remarks</span></span>  
 <span data-ttu-id="cc520-110">Os ganchos [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)e [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) fornecem inspeção de quadro de pilha e de argumentos.</span><span class="sxs-lookup"><span data-stu-id="cc520-110">The [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) hooks provide stack frame and argument inspection.</span></span> <span data-ttu-id="cc520-111">Para acessar essas informações, os sinalizadores `COR_PRF_ENABLE_FUNCTION_ARGS`, `COR_PRF_ENABLE_FUNCTION_RETVAL`e/ou `COR_PRF_ENABLE_FRAME_INFO` devem ser definidos.</span><span class="sxs-lookup"><span data-stu-id="cc520-111">To access that information, the `COR_PRF_ENABLE_FUNCTION_ARGS`, `COR_PRF_ENABLE_FUNCTION_RETVAL`, and/or `COR_PRF_ENABLE_FRAME_INFO` flags have to be set.</span></span> <span data-ttu-id="cc520-112">O criador de perfil pode usar o método [ICorProfilerInfo:: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) para definir os sinalizadores de evento e, em seguida, usar o método `SetEnterLeaveFunctionHooks3WithInfo` para registrar a implementação dessa função.</span><span class="sxs-lookup"><span data-stu-id="cc520-112">The profiler can use the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the event flags, and then use the `SetEnterLeaveFunctionHooks3WithInfo` method to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="cc520-113">Somente um conjunto de retornos de chamada pode estar ativo por vez e a versão mais recente tem precedência.</span><span class="sxs-lookup"><span data-stu-id="cc520-113">Only one set of callbacks may be active at a time, and the newest version takes precedence.</span></span> <span data-ttu-id="cc520-114">Portanto, se um criador de perfil chamar [SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md) e `SetEnterLeaveFunctionHooks3WithInfo`, `SetEnterLeaveFunctionHooks3WithInfo` será usado.</span><span class="sxs-lookup"><span data-stu-id="cc520-114">Therefore, if a profiler calls both [SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md) and `SetEnterLeaveFunctionHooks3WithInfo`, `SetEnterLeaveFunctionHooks3WithInfo` is used.</span></span>  
  
 <span data-ttu-id="cc520-115">O método `SetEnterLeaveFunctionHooks3WithInfo` pode ser chamado somente do retorno de chamada [ICorProfilerCallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) do criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="cc520-115">The `SetEnterLeaveFunctionHooks3WithInfo` method may be called only from the profiler's [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc520-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cc520-116">Requirements</span></span>  
 <span data-ttu-id="cc520-117">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc520-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc520-118">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="cc520-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cc520-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cc520-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cc520-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc520-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc520-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cc520-121">See also</span></span>

- [<span data-ttu-id="cc520-122">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="cc520-122">SetEnterLeaveFunctionHooks3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="cc520-123">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="cc520-123">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)
- [<span data-ttu-id="cc520-124">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="cc520-124">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)
- [<span data-ttu-id="cc520-125">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="cc520-125">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [<span data-ttu-id="cc520-126">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="cc520-126">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [<span data-ttu-id="cc520-127">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="cc520-127">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [<span data-ttu-id="cc520-128">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="cc520-128">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [<span data-ttu-id="cc520-129">Criando perfil de funções estáticas globais</span><span class="sxs-lookup"><span data-stu-id="cc520-129">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
- [<span data-ttu-id="cc520-130">Interface ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="cc520-130">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="cc520-131">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="cc520-131">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="cc520-132">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="cc520-132">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
