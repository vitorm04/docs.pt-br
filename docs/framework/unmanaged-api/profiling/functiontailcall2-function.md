---
title: Função FunctionTailcall2
ms.date: 03/30/2017
api_name:
- FunctionTailcall2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall2
helpviewer_keywords:
- FunctionTailcall2 function [.NET Framework profiling]
ms.assetid: 249f9892-b5a9-41e1-b329-28a925904df6
topic_type:
- apiref
ms.openlocfilehash: 60276327617ae24e9bdcebf958613c21d3808429
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175181"
---
# <a name="functiontailcall2-function"></a><span data-ttu-id="7f1bc-102">Função FunctionTailcall2</span><span class="sxs-lookup"><span data-stu-id="7f1bc-102">FunctionTailcall2 Function</span></span>
<span data-ttu-id="7f1bc-103">Notifica o profiler de que a função de execução atualmente está prestes a executar uma chamada de cauda para outra função e fornece informações sobre o quadro de pilha.</span><span class="sxs-lookup"><span data-stu-id="7f1bc-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function and provides information about the stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f1bc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7f1bc-104">Syntax</span></span>  
  
```cpp
void __stdcall FunctionTailcall2 (  
    [in] FunctionID         funcId,
    [in] UINT_PTR           clientData,
    [in] COR_PRF_FRAME_INFO func  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7f1bc-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="7f1bc-105">Parameters</span></span>

- `funcId`

  <span data-ttu-id="7f1bc-106">\[em] O identificador da função de execução atual que está prestes a fazer uma chamada de cauda.</span><span class="sxs-lookup"><span data-stu-id="7f1bc-106">\[in] The identifier of the currently executing function that is about to make a tail call.</span></span>

- `clientData`

  <span data-ttu-id="7f1bc-107">\[em] O identificador de função remapped, que o profiler previamente especificado via [FunctionIDMapper](functionidmapper-function.md), da função de execução atual que está prestes a fazer uma chamada de cauda.</span><span class="sxs-lookup"><span data-stu-id="7f1bc-107">\[in] The remapped function identifier, which the profiler previously specified via [FunctionIDMapper](functionidmapper-function.md), of the currently executing function that is about to make a tail call.</span></span>
  
- `func`

  <span data-ttu-id="7f1bc-108">\[em] `COR_PRF_FRAME_INFO` Um valor que aponta para informações sobre o quadro de pilha.</span><span class="sxs-lookup"><span data-stu-id="7f1bc-108">\[in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>

  <span data-ttu-id="7f1bc-109">O profiler deve tratá-lo como uma alça opaca que pode ser passada de volta para o mecanismo de execução no método [ICorProfilerInfo2::GetFunctionInfo2.](icorprofilerinfo2-getfunctioninfo2-method.md)</span><span class="sxs-lookup"><span data-stu-id="7f1bc-109">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>

## <a name="remarks"></a><span data-ttu-id="7f1bc-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="7f1bc-110">Remarks</span></span>  
 <span data-ttu-id="7f1bc-111">A função de destino da chamada de cauda usará o quadro de pilha atual e retornará diretamente ao chamador da função que fez a chamada traseira.</span><span class="sxs-lookup"><span data-stu-id="7f1bc-111">The target function of the tail call will use the current stack frame, and will return directly to the caller of the function that made the tail call.</span></span> <span data-ttu-id="7f1bc-112">Isso significa que um retorno de chamada [FunctionLeave2](functionleave2-function.md) não será emitido para uma função que é o alvo de uma chamada de cauda.</span><span class="sxs-lookup"><span data-stu-id="7f1bc-112">This means that a [FunctionLeave2](functionleave2-function.md) callback will not be issued for a function that is the target of a tail call.</span></span>  
  
 <span data-ttu-id="7f1bc-113">O valor `func` do parâmetro não é `FunctionTailcall2` válido após o retorno da função porque o valor pode mudar ou ser destruído.</span><span class="sxs-lookup"><span data-stu-id="7f1bc-113">The value of the `func` parameter is not valid after the `FunctionTailcall2` function returns because the value may change or be destroyed.</span></span>  
  
 <span data-ttu-id="7f1bc-114">A `FunctionTailcall2` função é um retorno de chamada; você deve implementá-lo.</span><span class="sxs-lookup"><span data-stu-id="7f1bc-114">The `FunctionTailcall2` function is a callback; you must implement it.</span></span> <span data-ttu-id="7f1bc-115">A implementação `__declspec`deve`naked`usar o atributo () classe de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="7f1bc-115">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="7f1bc-116">O motor de execução não salva nenhum registro antes de chamar esta função.</span><span class="sxs-lookup"><span data-stu-id="7f1bc-116">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="7f1bc-117">Na entrada, você deve salvar todos os registros que você usa, incluindo os da unidade de ponto flutuante (FPU).</span><span class="sxs-lookup"><span data-stu-id="7f1bc-117">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="7f1bc-118">Na saída, você deve restaurar a pilha, atirando todos os parâmetros que foram empurrados pelo seu interlocutor.</span><span class="sxs-lookup"><span data-stu-id="7f1bc-118">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="7f1bc-119">A implantação `FunctionTailcall2` não deve bloquear porque vai atrasar a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="7f1bc-119">The implementation of `FunctionTailcall2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="7f1bc-120">A implementação não deve tentar uma coleta de lixo porque a pilha pode não estar em um estado favorável à coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="7f1bc-120">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="7f1bc-121">Se uma coleta de lixo for tentada, o tempo de execução será bloqueado até `FunctionTailcall2` o retorno.</span><span class="sxs-lookup"><span data-stu-id="7f1bc-121">If a garbage collection is attempted, the runtime will block until `FunctionTailcall2` returns.</span></span>  
  
 <span data-ttu-id="7f1bc-122">Além disso, a `FunctionTailcall2` função não deve chamar para código gerenciado ou de qualquer forma causar uma alocação de memória gerenciada.</span><span class="sxs-lookup"><span data-stu-id="7f1bc-122">Also, the `FunctionTailcall2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f1bc-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7f1bc-123">Requirements</span></span>  
 <span data-ttu-id="7f1bc-124">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f1bc-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f1bc-125">**Cabeçalho:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="7f1bc-125">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="7f1bc-126">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7f1bc-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7f1bc-127">**.NET Framework Versions:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f1bc-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f1bc-128">Confira também</span><span class="sxs-lookup"><span data-stu-id="7f1bc-128">See also</span></span>

- [<span data-ttu-id="7f1bc-129">Função FunctionEnter2</span><span class="sxs-lookup"><span data-stu-id="7f1bc-129">FunctionEnter2 Function</span></span>](functionenter2-function.md)
- [<span data-ttu-id="7f1bc-130">Função FunctionLeave2</span><span class="sxs-lookup"><span data-stu-id="7f1bc-130">FunctionLeave2 Function</span></span>](functionleave2-function.md)
- [<span data-ttu-id="7f1bc-131">Método SetEnterLeaveFunctionHooks2</span><span class="sxs-lookup"><span data-stu-id="7f1bc-131">SetEnterLeaveFunctionHooks2 Method</span></span>](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="7f1bc-132">Criando perfil de funções estáticas globais</span><span class="sxs-lookup"><span data-stu-id="7f1bc-132">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
