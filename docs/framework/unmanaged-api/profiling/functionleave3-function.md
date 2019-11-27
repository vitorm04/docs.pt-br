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
ms.openlocfilehash: 104a6c3c42c310513040cb45db7f51ffe729c19d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427443"
---
# <a name="functionleave3-function"></a><span data-ttu-id="12f1a-102">Função FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="12f1a-102">FunctionLeave3 Function</span></span>
<span data-ttu-id="12f1a-103">Notifica o criador de perfil que o controle está sendo retornado de uma função.</span><span class="sxs-lookup"><span data-stu-id="12f1a-103">Notifies the profiler that control is being returned from a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12f1a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="12f1a-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionLeave3(FunctionOrRemappedID functionOrRemappedID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="12f1a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="12f1a-105">Parameters</span></span>  
 `functionOrRemappedID`  
 <span data-ttu-id="12f1a-106">no O identificador da função da qual o controle é retornado.</span><span class="sxs-lookup"><span data-stu-id="12f1a-106">[in] The identifier of the function from which control is returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="12f1a-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="12f1a-107">Remarks</span></span>  
 <span data-ttu-id="12f1a-108">A função de retorno de chamada `FunctionLeave3` notifica o criador de perfil conforme as funções estão sendo chamadas, mas não oferece suporte à inspeção de valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="12f1a-108">The `FunctionLeave3` callback function notifies the profiler as functions are being called, but does not support return value inspection.</span></span> <span data-ttu-id="12f1a-109">Use o [método ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) para registrar sua implementação dessa função.</span><span class="sxs-lookup"><span data-stu-id="12f1a-109">Use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="12f1a-110">A função `FunctionLeave3` é um retorno de chamada; Você deve implementá-lo.</span><span class="sxs-lookup"><span data-stu-id="12f1a-110">The `FunctionLeave3` function is a callback; you must implement it.</span></span> <span data-ttu-id="12f1a-111">A implementação deve usar o `__declspec(naked)` atributo de classe de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="12f1a-111">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="12f1a-112">O mecanismo de execução não salva nenhum registro antes de chamar essa função.</span><span class="sxs-lookup"><span data-stu-id="12f1a-112">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="12f1a-113">Na entrada, você deve salvar todos os registros que usar, incluindo aqueles na FPU (unidade de ponto flutuante).</span><span class="sxs-lookup"><span data-stu-id="12f1a-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="12f1a-114">Ao sair, você deve restaurar a pilha removendo todos os parâmetros que foram enviados por Push por seu chamador.</span><span class="sxs-lookup"><span data-stu-id="12f1a-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="12f1a-115">A implementação de `FunctionLeave3` não deve bloquear, pois atrasará a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="12f1a-115">The implementation of `FunctionLeave3` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="12f1a-116">A implementação não deve tentar uma coleta de lixo, pois a pilha pode não estar em um estado amigável de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="12f1a-116">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="12f1a-117">Se uma coleta de lixo for tentada, o tempo de execução será bloqueado até que `FunctionLeave3` retorne.</span><span class="sxs-lookup"><span data-stu-id="12f1a-117">If a garbage collection is attempted, the runtime will block until `FunctionLeave3` returns.</span></span>  
  
 <span data-ttu-id="12f1a-118">A função `FunctionLeave3` não deve chamar um código gerenciado ou causar uma alocação de memória gerenciada de qualquer forma.</span><span class="sxs-lookup"><span data-stu-id="12f1a-118">The `FunctionLeave3` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12f1a-119">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="12f1a-119">Requirements</span></span>  
 <span data-ttu-id="12f1a-120">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12f1a-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12f1a-121">**Cabeçalho:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="12f1a-121">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="12f1a-122">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="12f1a-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="12f1a-123">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12f1a-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12f1a-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="12f1a-124">See also</span></span>

- [<span data-ttu-id="12f1a-125">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="12f1a-125">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)
- [<span data-ttu-id="12f1a-126">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="12f1a-126">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [<span data-ttu-id="12f1a-127">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="12f1a-127">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [<span data-ttu-id="12f1a-128">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="12f1a-128">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [<span data-ttu-id="12f1a-129">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="12f1a-129">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [<span data-ttu-id="12f1a-130">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="12f1a-130">SetEnterLeaveFunctionHooks3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="12f1a-131">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="12f1a-131">SetEnterLeaveFunctionHooks3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="12f1a-132">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="12f1a-132">SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="12f1a-133">SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="12f1a-133">SetFunctionIDMapper2</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="12f1a-134">Criando perfil de funções estáticas globais</span><span class="sxs-lookup"><span data-stu-id="12f1a-134">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
