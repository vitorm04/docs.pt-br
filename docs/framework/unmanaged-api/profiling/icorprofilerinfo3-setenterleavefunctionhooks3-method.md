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
ms.openlocfilehash: 3e07d2b61e85bb626613c40832c1a6aa499ef248
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868493"
---
# <a name="icorprofilerinfo3setenterleavefunctionhooks3-method"></a><span data-ttu-id="00f6b-102">Método ICorProfilerInfo3::SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="00f6b-102">ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 Method</span></span>
<span data-ttu-id="00f6b-103">Especifica as funções implementadas pelo criador de perfil que serão chamadas nas funções [FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md)e [FunctionTailcall3](functiontailcall3-function.md) .</span><span class="sxs-lookup"><span data-stu-id="00f6b-103">Specifies the profiler-implemented functions that will be called on the [FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md), and [FunctionTailcall3](functiontailcall3-function.md) functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00f6b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="00f6b-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks3(  
            [in] FunctionEnter3    *pFuncEnter3,  
            [in] FunctionLeave3    *pFuncLeave3,  
            [in] FunctionTailcall3 *pFuncTailcall3);  
```  
  
## <a name="parameters"></a><span data-ttu-id="00f6b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="00f6b-105">Parameters</span></span>  
 `pFuncEnter3`  
 <span data-ttu-id="00f6b-106">no Um ponteiro para a implementação a ser usado como o retorno de chamada `FunctionEnter3`.</span><span class="sxs-lookup"><span data-stu-id="00f6b-106">[in] A pointer to the implementation to be used as the `FunctionEnter3` callback.</span></span>  
  
 `pFuncLeave3`  
 <span data-ttu-id="00f6b-107">no Um ponteiro para a implementação a ser usado como o retorno de chamada `FunctionLeave3`.</span><span class="sxs-lookup"><span data-stu-id="00f6b-107">[in] A pointer to the implementation to be used as the `FunctionLeave3` callback.</span></span>  
  
 `pFuncTailcall3`  
 <span data-ttu-id="00f6b-108">no Um ponteiro para a implementação a ser usado como o retorno de chamada `FunctionTailcall3`.</span><span class="sxs-lookup"><span data-stu-id="00f6b-108">[in] A pointer to the implementation to be used as the `FunctionTailcall3` callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="00f6b-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="00f6b-109">Remarks</span></span>  
 <span data-ttu-id="00f6b-110">Os ganchos [FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md)e [FunctionTailcall3](functiontailcall3-function.md) não fornecem inspeção de quadro de pilha e de argumentos.</span><span class="sxs-lookup"><span data-stu-id="00f6b-110">[FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md), and [FunctionTailcall3](functiontailcall3-function.md) hooks do not provide stack frame and argument inspection.</span></span> <span data-ttu-id="00f6b-111">Para acessar essas informações, os sinalizadores `COR_PRF_ENABLE_FUNCTION_ARGS`, `COR_PRF_ENABLE_FUNCTION_RETVAL`e/ou `COR_PRF_ENABLE_FRAME_INFO` devem ser definidos.</span><span class="sxs-lookup"><span data-stu-id="00f6b-111">To access that information, the `COR_PRF_ENABLE_FUNCTION_ARGS`, `COR_PRF_ENABLE_FUNCTION_RETVAL`, and/or  `COR_PRF_ENABLE_FRAME_INFO` flags have to be set.</span></span> <span data-ttu-id="00f6b-112">O criador de perfil pode usar o método [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) para definir os sinalizadores de evento e, em seguida, usar o método [ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3WithInfo](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) para registrar sua implementação dessa função.</span><span class="sxs-lookup"><span data-stu-id="00f6b-112">The profiler can use the [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) method to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) method to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="00f6b-113">Somente um conjunto de retornos de chamada pode estar ativo por vez e a versão mais recente tem precedência.</span><span class="sxs-lookup"><span data-stu-id="00f6b-113">Only one set of callbacks may be active at a time, and the newest version takes precedence.</span></span> <span data-ttu-id="00f6b-114">Portanto, se um criador de perfil chamar o [método SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md) e o método `SetEnterLeaveFunctionHooks3`, `SetEnterLeaveFunctionHooks3` será usado.</span><span class="sxs-lookup"><span data-stu-id="00f6b-114">Therefore, if a profiler calls both the [SetEnterLeaveFunctionHooks2 Method](icorprofilerinfo2-setenterleavefunctionhooks2-method.md) and the `SetEnterLeaveFunctionHooks3` method, `SetEnterLeaveFunctionHooks3` is used.</span></span>  
  
 <span data-ttu-id="00f6b-115">O método `SetEnterLeaveFunctionHooks3` pode ser chamado somente do retorno de chamada [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) do criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="00f6b-115">The `SetEnterLeaveFunctionHooks3` method may be called only from the profiler's [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00f6b-116">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="00f6b-116">Requirements</span></span>  
 <span data-ttu-id="00f6b-117">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00f6b-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00f6b-118">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="00f6b-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="00f6b-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="00f6b-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="00f6b-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00f6b-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00f6b-121">Veja também</span><span class="sxs-lookup"><span data-stu-id="00f6b-121">See also</span></span>

- [<span data-ttu-id="00f6b-122">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="00f6b-122">SetEnterLeaveFunctionHooks3WithInfo</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="00f6b-123">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="00f6b-123">FunctionEnter3</span></span>](functionenter3-function.md)
- [<span data-ttu-id="00f6b-124">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="00f6b-124">FunctionLeave3</span></span>](functionleave3-function.md)
- [<span data-ttu-id="00f6b-125">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="00f6b-125">FunctionTailcall3</span></span>](functiontailcall3-function.md)
- [<span data-ttu-id="00f6b-126">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="00f6b-126">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="00f6b-127">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="00f6b-127">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="00f6b-128">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="00f6b-128">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="00f6b-129">Criando perfil de funções estáticas globais</span><span class="sxs-lookup"><span data-stu-id="00f6b-129">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
- [<span data-ttu-id="00f6b-130">ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="00f6b-130">ICorProfilerInfo3</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="00f6b-131">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="00f6b-131">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="00f6b-132">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="00f6b-132">Profiling</span></span>](index.md)
