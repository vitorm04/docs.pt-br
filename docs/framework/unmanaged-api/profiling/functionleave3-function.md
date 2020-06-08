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
ms.openlocfilehash: 456d9a0e8236948ac69ed069495b1999ebf7e80a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500605"
---
# <a name="functionleave3-function"></a><span data-ttu-id="0e87c-102">Função FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="0e87c-102">FunctionLeave3 Function</span></span>
<span data-ttu-id="0e87c-103">Notifica o criador de perfil que o controle está sendo retornado de uma função.</span><span class="sxs-lookup"><span data-stu-id="0e87c-103">Notifies the profiler that control is being returned from a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e87c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0e87c-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionLeave3(FunctionOrRemappedID functionOrRemappedID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0e87c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0e87c-105">Parameters</span></span>  

- `functionOrRemappedID`

  <span data-ttu-id="0e87c-106">\[in] o identificador da função a partir da qual o controle é retornado.</span><span class="sxs-lookup"><span data-stu-id="0e87c-106">\[in] The identifier of the function from which control is returned.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="0e87c-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="0e87c-107">Remarks</span></span>  
 <span data-ttu-id="0e87c-108">A `FunctionLeave3` função de retorno de chamada notifica o criador de perfil conforme as funções estão sendo chamadas, mas não oferece suporte à inspeção de valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="0e87c-108">The `FunctionLeave3` callback function notifies the profiler as functions are being called, but does not support return value inspection.</span></span> <span data-ttu-id="0e87c-109">Use o [método ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) para registrar sua implementação dessa função.</span><span class="sxs-lookup"><span data-stu-id="0e87c-109">Use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="0e87c-110">A `FunctionLeave3` função é um retorno de chamada; você deve implementá-la.</span><span class="sxs-lookup"><span data-stu-id="0e87c-110">The `FunctionLeave3` function is a callback; you must implement it.</span></span> <span data-ttu-id="0e87c-111">A implementação deve usar o `__declspec(naked)` atributo de classe de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="0e87c-111">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="0e87c-112">O mecanismo de execução não salva nenhum registro antes de chamar essa função.</span><span class="sxs-lookup"><span data-stu-id="0e87c-112">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="0e87c-113">Na entrada, você deve salvar todos os registros que usar, incluindo aqueles na FPU (unidade de ponto flutuante).</span><span class="sxs-lookup"><span data-stu-id="0e87c-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="0e87c-114">Ao sair, você deve restaurar a pilha removendo todos os parâmetros que foram enviados por Push por seu chamador.</span><span class="sxs-lookup"><span data-stu-id="0e87c-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="0e87c-115">A implementação de `FunctionLeave3` não deve bloquear, pois atrasará a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="0e87c-115">The implementation of `FunctionLeave3` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="0e87c-116">A implementação não deve tentar uma coleta de lixo, pois a pilha pode não estar em um estado amigável de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="0e87c-116">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="0e87c-117">Se for feita uma tentativa de coleta de lixo, o tempo de execução será bloqueado até o `FunctionLeave3` retorno.</span><span class="sxs-lookup"><span data-stu-id="0e87c-117">If a garbage collection is attempted, the runtime will block until `FunctionLeave3` returns.</span></span>  
  
 <span data-ttu-id="0e87c-118">A `FunctionLeave3` função não deve chamar código gerenciado ou causar uma alocação de memória gerenciada de qualquer forma.</span><span class="sxs-lookup"><span data-stu-id="0e87c-118">The `FunctionLeave3` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e87c-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0e87c-119">Requirements</span></span>  
 <span data-ttu-id="0e87c-120">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e87c-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e87c-121">**Cabeçalho:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="0e87c-121">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="0e87c-122">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0e87c-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0e87c-123">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e87c-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e87c-124">Confira também</span><span class="sxs-lookup"><span data-stu-id="0e87c-124">See also</span></span>

- [<span data-ttu-id="0e87c-125">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="0e87c-125">FunctionEnter3</span></span>](functionenter3-function.md)
- [<span data-ttu-id="0e87c-126">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="0e87c-126">FunctionTailcall3</span></span>](functiontailcall3-function.md)
- [<span data-ttu-id="0e87c-127">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="0e87c-127">FunctionEnter3WithInfo</span></span>](functiontailcall3-function.md)
- [<span data-ttu-id="0e87c-128">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="0e87c-128">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="0e87c-129">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="0e87c-129">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="0e87c-130">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="0e87c-130">SetEnterLeaveFunctionHooks3</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="0e87c-131">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="0e87c-131">SetEnterLeaveFunctionHooks3WithInfo</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="0e87c-132">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="0e87c-132">SetFunctionIDMapper</span></span>](icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="0e87c-133">SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="0e87c-133">SetFunctionIDMapper2</span></span>](icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="0e87c-134">Criando perfil de funções estáticas globais</span><span class="sxs-lookup"><span data-stu-id="0e87c-134">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
