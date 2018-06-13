---
title: Função FunctionTailcall3
ms.date: 03/30/2017
api_name:
- FunctionTailcall3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall3
helpviewer_keywords:
- FunctionTailcall3 function [.NET Framework profiling]
ms.assetid: 1e48243f-5de6-4bd6-a1d0-e1d248bca4b8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 82d718c6f6aee36f3a916eb7f9b9a1e0b3b46cb5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452462"
---
# <a name="functiontailcall3-function"></a><span data-ttu-id="df80c-102">Função FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="df80c-102">FunctionTailcall3 Function</span></span>
<span data-ttu-id="df80c-103">Notifica o criador de perfil que a função atualmente em execução está prestes a realizar uma chamada tail para outra função.</span><span class="sxs-lookup"><span data-stu-id="df80c-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df80c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="df80c-104">Syntax</span></span>  
  
```  
void __stdcall FunctionTailcall3 (FunctionOrRemappedID functionOrRemappedID);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="df80c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="df80c-105">Parameters</span></span>  
 `functionOrRemappedID`  
 <span data-ttu-id="df80c-106">[in] O identificador da função atualmente em execução que está prestes a fazer uma cauda chamada.</span><span class="sxs-lookup"><span data-stu-id="df80c-106">[in] The identifier of the currently executing function that is about to make a tail call.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="df80c-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="df80c-107">Remarks</span></span>  
 <span data-ttu-id="df80c-108">O `FunctionTailcall3` função de retorno de chamada notifica o criador de perfil como funções estão sendo chamadas.</span><span class="sxs-lookup"><span data-stu-id="df80c-108">The `FunctionTailcall3` callback function notifies the profiler as functions are being called.</span></span> <span data-ttu-id="df80c-109">Use o [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 método](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) para registrar sua implementação dessa função.</span><span class="sxs-lookup"><span data-stu-id="df80c-109">Use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="df80c-110">O `FunctionTailcall3` função é um retorno de chamada; você deve implementá-la.</span><span class="sxs-lookup"><span data-stu-id="df80c-110">The `FunctionTailcall3` function is a callback; you must implement it.</span></span> <span data-ttu-id="df80c-111">A implementação deve usar o `__declspec(naked)` atributo de classe de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="df80c-111">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="df80c-112">O mecanismo de execução não salva quaisquer registros antes de chamar essa função.</span><span class="sxs-lookup"><span data-stu-id="df80c-112">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="df80c-113">Na entrada, você deve salvar todos os registros que você usa, incluindo aqueles na unidade de ponto flutuante (FPU).</span><span class="sxs-lookup"><span data-stu-id="df80c-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="df80c-114">Na saída, você deve restaurar a pilha por retirar desativar todos os parâmetros que foram empurrados pelo chamador.</span><span class="sxs-lookup"><span data-stu-id="df80c-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="df80c-115">A implementação de `FunctionTailcall3` não devem bloquear, porque ele atrasará a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="df80c-115">The implementation of `FunctionTailcall3` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="df80c-116">A implementação não deve tentar uma coleta de lixo, porque a pilha pode não estar em um estado de amigável para coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="df80c-116">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="df80c-117">Se você tentar uma coleta de lixo, tempo de execução será bloqueado até que `FunctionTailcall3` retorna.</span><span class="sxs-lookup"><span data-stu-id="df80c-117">If a garbage collection is attempted, the runtime will block until `FunctionTailcall3` returns.</span></span>  
  
 <span data-ttu-id="df80c-118">O `FunctionTailcall3` função não deve chamar código gerenciado ou fazer com que uma alocação de memória gerenciada de forma alguma.</span><span class="sxs-lookup"><span data-stu-id="df80c-118">The `FunctionTailcall3` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df80c-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="df80c-119">Requirements</span></span>  
 <span data-ttu-id="df80c-120">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df80c-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df80c-121">**Cabeçalho:** Corprof. idl</span><span class="sxs-lookup"><span data-stu-id="df80c-121">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="df80c-122">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="df80c-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="df80c-123">**Versões do .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df80c-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df80c-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="df80c-124">See Also</span></span>  
 [<span data-ttu-id="df80c-125">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="df80c-125">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)  
 [<span data-ttu-id="df80c-126">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="df80c-126">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)  
 [<span data-ttu-id="df80c-127">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="df80c-127">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)  
 [<span data-ttu-id="df80c-128">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="df80c-128">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 [<span data-ttu-id="df80c-129">Função FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="df80c-129">FunctionTailcall3WithInfo Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 [<span data-ttu-id="df80c-130">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="df80c-130">SetEnterLeaveFunctionHooks3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)  
 [<span data-ttu-id="df80c-131">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="df80c-131">SetEnterLeaveFunctionHooks3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)  
 [<span data-ttu-id="df80c-132">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="df80c-132">SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)  
 [<span data-ttu-id="df80c-133">SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="df80c-133">SetFunctionIDMapper2</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)  
 [<span data-ttu-id="df80c-134">Criando perfil de funções estáticas globais</span><span class="sxs-lookup"><span data-stu-id="df80c-134">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
