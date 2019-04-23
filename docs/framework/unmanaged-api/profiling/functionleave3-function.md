---
title: Função FunctionLeave3
ms.date: 03/30/2017
api_name:
- FunctionLeave3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionLeave3
helpviewer_keywords:
- FunctionLeave3 function [.NET Framework profiling]
ms.assetid: 5d798088-7992-48a0-ae55-d2a7ee31913f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b31c3045b021bd3b00d2b2e42bf7a118110305b1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59099879"
---
# <a name="functionleave3-function"></a><span data-ttu-id="94033-102">Função FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="94033-102">FunctionLeave3 Function</span></span>
<span data-ttu-id="94033-103">Notifica o criador de perfil que o controle está sendo retornado de uma função.</span><span class="sxs-lookup"><span data-stu-id="94033-103">Notifies the profiler that control is being returned from a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94033-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="94033-104">Syntax</span></span>  
  
```  
void __stdcall FunctionLeave3(FunctionOrRemappedID functionOrRemappedID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="94033-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="94033-105">Parameters</span></span>  
 `functionOrRemappedID`  
 <span data-ttu-id="94033-106">[in] O identificador da função da qual o controle é retornado.</span><span class="sxs-lookup"><span data-stu-id="94033-106">[in] The identifier of the function from which control is returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="94033-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="94033-107">Remarks</span></span>  
 <span data-ttu-id="94033-108">O `FunctionLeave3` função de retorno de chamada notifica o criador de perfil como funções estão sendo chamados, mas não oferece suporte a inspeção do valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="94033-108">The `FunctionLeave3` callback function notifies the profiler as functions are being called, but does not support return value inspection.</span></span> <span data-ttu-id="94033-109">Use o [método ICorProfilerInfo3::SetEnterLeaveFunctionHooks3](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) para registrar sua implementação dessa função.</span><span class="sxs-lookup"><span data-stu-id="94033-109">Use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="94033-110">O `FunctionLeave3` função é um retorno de chamada; você deve implementá-la.</span><span class="sxs-lookup"><span data-stu-id="94033-110">The `FunctionLeave3` function is a callback; you must implement it.</span></span> <span data-ttu-id="94033-111">A implementação deve usar o `__declspec(naked)` atributo de classe de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="94033-111">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="94033-112">O mecanismo de execução não salva qualquer registros antes de chamar essa função.</span><span class="sxs-lookup"><span data-stu-id="94033-112">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="94033-113">Na entrada, você deve salvar todos os registros que você usa, incluindo aqueles na unidade de ponto flutuante (FPU).</span><span class="sxs-lookup"><span data-stu-id="94033-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="94033-114">Na saída, você deve restaurar a pilha de popping desativar todos os parâmetros que foram enviados por push ao seu chamador.</span><span class="sxs-lookup"><span data-stu-id="94033-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="94033-115">A implementação de `FunctionLeave3` não devem bloquear, porque isso atrasará a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="94033-115">The implementation of `FunctionLeave3` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="94033-116">A implementação não deve tentar uma coleta de lixo, porque a pilha não pode estar em um estado de amigável para coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="94033-116">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="94033-117">Se você tentar uma coleta de lixo, o tempo de execução será bloqueado até que `FunctionLeave3` retorna.</span><span class="sxs-lookup"><span data-stu-id="94033-117">If a garbage collection is attempted, the runtime will block until `FunctionLeave3` returns.</span></span>  
  
 <span data-ttu-id="94033-118">O `FunctionLeave3` função não deve chamar código gerenciado ou fazer com que uma alocação de memória gerenciada de forma alguma.</span><span class="sxs-lookup"><span data-stu-id="94033-118">The `FunctionLeave3` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94033-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="94033-119">Requirements</span></span>  
 <span data-ttu-id="94033-120">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="94033-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94033-121">**Cabeçalho:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="94033-121">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="94033-122">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="94033-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="94033-123">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94033-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94033-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="94033-124">See also</span></span>

- [<span data-ttu-id="94033-125">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="94033-125">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)
- [<span data-ttu-id="94033-126">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="94033-126">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [<span data-ttu-id="94033-127">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="94033-127">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [<span data-ttu-id="94033-128">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="94033-128">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [<span data-ttu-id="94033-129">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="94033-129">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [<span data-ttu-id="94033-130">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="94033-130">SetEnterLeaveFunctionHooks3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="94033-131">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="94033-131">SetEnterLeaveFunctionHooks3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="94033-132">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="94033-132">SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="94033-133">SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="94033-133">SetFunctionIDMapper2</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="94033-134">Criando perfil de funções estáticas globais</span><span class="sxs-lookup"><span data-stu-id="94033-134">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
