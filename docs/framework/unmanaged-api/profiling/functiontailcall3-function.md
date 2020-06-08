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
ms.openlocfilehash: 55955cd47bd32fb4294b0b8e852dd692702bd74f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500527"
---
# <a name="functiontailcall3-function"></a><span data-ttu-id="d106a-102">Função FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="d106a-102">FunctionTailcall3 Function</span></span>
<span data-ttu-id="d106a-103">Notifica o criador de perfil de que a função atualmente em execução está prestes a executar uma chamada tail para outra função.</span><span class="sxs-lookup"><span data-stu-id="d106a-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d106a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d106a-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionTailcall3 (FunctionOrRemappedID functionOrRemappedID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d106a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d106a-105">Parameters</span></span>

- `functionOrRemappedID`

  <span data-ttu-id="d106a-106">\[in] o identificador da função atualmente em execução que está prestes a fazer uma chamada tail.</span><span class="sxs-lookup"><span data-stu-id="d106a-106">\[in] The identifier of the currently executing function that is about to make a tail call.</span></span>

## <a name="remarks"></a><span data-ttu-id="d106a-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="d106a-107">Remarks</span></span>  
 <span data-ttu-id="d106a-108">A `FunctionTailcall3` função de retorno de chamada notifica o criador de perfil conforme as funções estão sendo chamadas.</span><span class="sxs-lookup"><span data-stu-id="d106a-108">The `FunctionTailcall3` callback function notifies the profiler as functions are being called.</span></span> <span data-ttu-id="d106a-109">Use o [método ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) para registrar sua implementação dessa função.</span><span class="sxs-lookup"><span data-stu-id="d106a-109">Use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="d106a-110">A `FunctionTailcall3` função é um retorno de chamada; você deve implementá-la.</span><span class="sxs-lookup"><span data-stu-id="d106a-110">The `FunctionTailcall3` function is a callback; you must implement it.</span></span> <span data-ttu-id="d106a-111">A implementação deve usar o `__declspec(naked)` atributo de classe de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="d106a-111">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="d106a-112">O mecanismo de execução não salva nenhum registro antes de chamar essa função.</span><span class="sxs-lookup"><span data-stu-id="d106a-112">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="d106a-113">Na entrada, você deve salvar todos os registros que usar, incluindo aqueles na FPU (unidade de ponto flutuante).</span><span class="sxs-lookup"><span data-stu-id="d106a-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="d106a-114">Ao sair, você deve restaurar a pilha removendo todos os parâmetros que foram enviados por Push por seu chamador.</span><span class="sxs-lookup"><span data-stu-id="d106a-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="d106a-115">A implementação de `FunctionTailcall3` não deve bloquear, pois atrasará a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="d106a-115">The implementation of `FunctionTailcall3` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="d106a-116">A implementação não deve tentar uma coleta de lixo, pois a pilha pode não estar em um estado amigável de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="d106a-116">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="d106a-117">Se for feita uma tentativa de coleta de lixo, o tempo de execução será bloqueado até o `FunctionTailcall3` retorno.</span><span class="sxs-lookup"><span data-stu-id="d106a-117">If a garbage collection is attempted, the runtime will block until `FunctionTailcall3` returns.</span></span>  
  
 <span data-ttu-id="d106a-118">A `FunctionTailcall3` função não deve chamar código gerenciado ou causar uma alocação de memória gerenciada de qualquer forma.</span><span class="sxs-lookup"><span data-stu-id="d106a-118">The `FunctionTailcall3` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d106a-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d106a-119">Requirements</span></span>  
 <span data-ttu-id="d106a-120">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d106a-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d106a-121">**Cabeçalho:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="d106a-121">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="d106a-122">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d106a-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d106a-123">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d106a-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d106a-124">Confira também</span><span class="sxs-lookup"><span data-stu-id="d106a-124">See also</span></span>

- [<span data-ttu-id="d106a-125">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="d106a-125">FunctionEnter3</span></span>](functionenter3-function.md)
- [<span data-ttu-id="d106a-126">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="d106a-126">FunctionLeave3</span></span>](functionleave3-function.md)
- [<span data-ttu-id="d106a-127">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="d106a-127">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="d106a-128">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="d106a-128">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="d106a-129">Função FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="d106a-129">FunctionTailcall3WithInfo Function</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="d106a-130">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="d106a-130">SetEnterLeaveFunctionHooks3</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="d106a-131">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="d106a-131">SetEnterLeaveFunctionHooks3WithInfo</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="d106a-132">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="d106a-132">SetFunctionIDMapper</span></span>](icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="d106a-133">SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="d106a-133">SetFunctionIDMapper2</span></span>](icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="d106a-134">Criando perfil de funções estáticas globais</span><span class="sxs-lookup"><span data-stu-id="d106a-134">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
