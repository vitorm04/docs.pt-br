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
ms.openlocfilehash: eb658d682ce589b7dfdcfc0228d0c657310e6f7a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496198"
---
# <a name="icorprofilerinfo3setenterleavefunctionhooks3-method"></a><span data-ttu-id="a38e3-102">Método ICorProfilerInfo3::SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="a38e3-102">ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 Method</span></span>
<span data-ttu-id="a38e3-103">Especifica as funções implementadas pelo criador de perfil que serão chamadas nas funções [FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md)e [FunctionTailcall3](functiontailcall3-function.md) .</span><span class="sxs-lookup"><span data-stu-id="a38e3-103">Specifies the profiler-implemented functions that will be called on the [FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md), and [FunctionTailcall3](functiontailcall3-function.md) functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a38e3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a38e3-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks3(  
            [in] FunctionEnter3    *pFuncEnter3,  
            [in] FunctionLeave3    *pFuncLeave3,  
            [in] FunctionTailcall3 *pFuncTailcall3);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a38e3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a38e3-105">Parameters</span></span>  
 `pFuncEnter3`  
 <span data-ttu-id="a38e3-106">no Um ponteiro para a implementação a ser usado como o `FunctionEnter3` retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="a38e3-106">[in] A pointer to the implementation to be used as the `FunctionEnter3` callback.</span></span>  
  
 `pFuncLeave3`  
 <span data-ttu-id="a38e3-107">no Um ponteiro para a implementação a ser usado como o `FunctionLeave3` retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="a38e3-107">[in] A pointer to the implementation to be used as the `FunctionLeave3` callback.</span></span>  
  
 `pFuncTailcall3`  
 <span data-ttu-id="a38e3-108">no Um ponteiro para a implementação a ser usado como o `FunctionTailcall3` retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="a38e3-108">[in] A pointer to the implementation to be used as the `FunctionTailcall3` callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a38e3-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="a38e3-109">Remarks</span></span>  
 <span data-ttu-id="a38e3-110">Os ganchos [FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md)e [FunctionTailcall3](functiontailcall3-function.md) não fornecem inspeção de quadro de pilha e de argumentos.</span><span class="sxs-lookup"><span data-stu-id="a38e3-110">[FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md), and [FunctionTailcall3](functiontailcall3-function.md) hooks do not provide stack frame and argument inspection.</span></span> <span data-ttu-id="a38e3-111">Para acessar essas informações, os `COR_PRF_ENABLE_FUNCTION_ARGS` `COR_PRF_ENABLE_FUNCTION_RETVAL` sinalizadores, e/ou `COR_PRF_ENABLE_FRAME_INFO` devem ser definidos.</span><span class="sxs-lookup"><span data-stu-id="a38e3-111">To access that information, the `COR_PRF_ENABLE_FUNCTION_ARGS`, `COR_PRF_ENABLE_FUNCTION_RETVAL`, and/or  `COR_PRF_ENABLE_FRAME_INFO` flags have to be set.</span></span> <span data-ttu-id="a38e3-112">O criador de perfil pode usar o método [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) para definir os sinalizadores de evento e, em seguida, usar o método [ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3WithInfo](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) para registrar sua implementação dessa função.</span><span class="sxs-lookup"><span data-stu-id="a38e3-112">The profiler can use the [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) method to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) method to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="a38e3-113">Somente um conjunto de retornos de chamada pode estar ativo por vez e a versão mais recente tem precedência.</span><span class="sxs-lookup"><span data-stu-id="a38e3-113">Only one set of callbacks may be active at a time, and the newest version takes precedence.</span></span> <span data-ttu-id="a38e3-114">Portanto, se um criador de perfil chamar o [método SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md) e o `SetEnterLeaveFunctionHooks3` método, `SetEnterLeaveFunctionHooks3` será usado.</span><span class="sxs-lookup"><span data-stu-id="a38e3-114">Therefore, if a profiler calls both the [SetEnterLeaveFunctionHooks2 Method](icorprofilerinfo2-setenterleavefunctionhooks2-method.md) and the `SetEnterLeaveFunctionHooks3` method, `SetEnterLeaveFunctionHooks3` is used.</span></span>  
  
 <span data-ttu-id="a38e3-115">O `SetEnterLeaveFunctionHooks3` método pode ser chamado somente do retorno de chamada [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) do criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="a38e3-115">The `SetEnterLeaveFunctionHooks3` method may be called only from the profiler's [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a38e3-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a38e3-116">Requirements</span></span>  
 <span data-ttu-id="a38e3-117">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a38e3-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a38e3-118">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="a38e3-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a38e3-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a38e3-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a38e3-120">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a38e3-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a38e3-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="a38e3-121">See also</span></span>

- [<span data-ttu-id="a38e3-122">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="a38e3-122">SetEnterLeaveFunctionHooks3WithInfo</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="a38e3-123">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="a38e3-123">FunctionEnter3</span></span>](functionenter3-function.md)
- [<span data-ttu-id="a38e3-124">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="a38e3-124">FunctionLeave3</span></span>](functionleave3-function.md)
- [<span data-ttu-id="a38e3-125">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="a38e3-125">FunctionTailcall3</span></span>](functiontailcall3-function.md)
- [<span data-ttu-id="a38e3-126">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="a38e3-126">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="a38e3-127">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="a38e3-127">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="a38e3-128">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="a38e3-128">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="a38e3-129">Criando perfil de funções estáticas globais</span><span class="sxs-lookup"><span data-stu-id="a38e3-129">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
- [<span data-ttu-id="a38e3-130">ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="a38e3-130">ICorProfilerInfo3</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="a38e3-131">Criação de perfil de interfaces</span><span class="sxs-lookup"><span data-stu-id="a38e3-131">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="a38e3-132">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="a38e3-132">Profiling</span></span>](index.md)
