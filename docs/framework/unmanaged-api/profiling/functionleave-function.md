---
title: Função FunctionLeave
ms.date: 03/30/2017
api_name:
- FunctionLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionLeave
helpviewer_keywords:
- FunctionLeave function [.NET Framework profiling]
ms.assetid: 18e89f45-e068-426a-be16-9f53a4346860
topic_type:
- apiref
ms.openlocfilehash: 774a5d4e48f00ea8c28977f3f685dcd5a8da3199
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440579"
---
# <a name="functionleave-function"></a><span data-ttu-id="7c1b0-102">Função FunctionLeave</span><span class="sxs-lookup"><span data-stu-id="7c1b0-102">FunctionLeave Function</span></span>
<span data-ttu-id="7c1b0-103">Notifies the profiler that a function is about to return to the caller.</span><span class="sxs-lookup"><span data-stu-id="7c1b0-103">Notifies the profiler that a function is about to return to the caller.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7c1b0-104">The `FunctionLeave` function is deprecated in the .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="7c1b0-104">The `FunctionLeave` function is deprecated in the .NET Framework 2.0.</span></span> <span data-ttu-id="7c1b0-105">It will continue to work, but will incur a performance penalty.</span><span class="sxs-lookup"><span data-stu-id="7c1b0-105">It will continue to work, but will incur a performance penalty.</span></span> <span data-ttu-id="7c1b0-106">Use the [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) function instead.</span><span class="sxs-lookup"><span data-stu-id="7c1b0-106">Use the [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c1b0-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7c1b0-107">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionLeave (  
    [in] FunctionID funcID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7c1b0-108">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7c1b0-108">Parameters</span></span>  
 `funcID`  
 <span data-ttu-id="7c1b0-109">[in] The identifier of the function that is returning.</span><span class="sxs-lookup"><span data-stu-id="7c1b0-109">[in] The identifier of the function that is returning.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7c1b0-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="7c1b0-110">Remarks</span></span>  
 <span data-ttu-id="7c1b0-111">The `FunctionLeave` function is a callback; you must implement it.</span><span class="sxs-lookup"><span data-stu-id="7c1b0-111">The `FunctionLeave` function is a callback; you must implement it.</span></span> <span data-ttu-id="7c1b0-112">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span><span class="sxs-lookup"><span data-stu-id="7c1b0-112">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="7c1b0-113">The execution engine does not save any registers before calling this function.</span><span class="sxs-lookup"><span data-stu-id="7c1b0-113">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="7c1b0-114">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span><span class="sxs-lookup"><span data-stu-id="7c1b0-114">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="7c1b0-115">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span><span class="sxs-lookup"><span data-stu-id="7c1b0-115">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="7c1b0-116">The implementation of `FunctionLeave` should not block because it will delay garbage collection.</span><span class="sxs-lookup"><span data-stu-id="7c1b0-116">The implementation of `FunctionLeave` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="7c1b0-117">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span><span class="sxs-lookup"><span data-stu-id="7c1b0-117">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="7c1b0-118">If a garbage collection is attempted, the runtime will block until `FunctionLeave` returns.</span><span class="sxs-lookup"><span data-stu-id="7c1b0-118">If a garbage collection is attempted, the runtime will block until `FunctionLeave` returns.</span></span>  
  
 <span data-ttu-id="7c1b0-119">Also, the `FunctionLeave` function must not call into managed code or in any way cause a managed memory allocation.</span><span class="sxs-lookup"><span data-stu-id="7c1b0-119">Also, the `FunctionLeave` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c1b0-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7c1b0-120">Requirements</span></span>  
 <span data-ttu-id="7c1b0-121">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c1b0-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c1b0-122">**Header:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="7c1b0-122">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="7c1b0-123">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7c1b0-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7c1b0-124">**.NET Framework Versions:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="7c1b0-124">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c1b0-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7c1b0-125">See also</span></span>

- [<span data-ttu-id="7c1b0-126">Função FunctionEnter2</span><span class="sxs-lookup"><span data-stu-id="7c1b0-126">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [<span data-ttu-id="7c1b0-127">Função FunctionLeave2</span><span class="sxs-lookup"><span data-stu-id="7c1b0-127">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [<span data-ttu-id="7c1b0-128">Função FunctionTailcall2</span><span class="sxs-lookup"><span data-stu-id="7c1b0-128">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)
- [<span data-ttu-id="7c1b0-129">Método SetEnterLeaveFunctionHooks2</span><span class="sxs-lookup"><span data-stu-id="7c1b0-129">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="7c1b0-130">Criando perfil de funções estáticas globais</span><span class="sxs-lookup"><span data-stu-id="7c1b0-130">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
