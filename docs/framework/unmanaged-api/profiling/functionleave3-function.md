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
ms.openlocfilehash: 32d86f19e9c50694c7d113195e6967645b710666
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866863"
---
# <a name="functionleave3-function"></a><span data-ttu-id="ac043-102">Função FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="ac043-102">FunctionLeave3 Function</span></span>
<span data-ttu-id="ac043-103">Notifica o criador de perfil que o controle está sendo retornado de uma função.</span><span class="sxs-lookup"><span data-stu-id="ac043-103">Notifies the profiler that control is being returned from a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac043-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ac043-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionLeave3(FunctionOrRemappedID functionOrRemappedID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ac043-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ac043-105">Parameters</span></span>  

- `functionOrRemappedID`

  <span data-ttu-id="ac043-106">\[em] o identificador da função da qual o controle é retornado.</span><span class="sxs-lookup"><span data-stu-id="ac043-106">\[in] The identifier of the function from which control is returned.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="ac043-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="ac043-107">Remarks</span></span>  
 <span data-ttu-id="ac043-108">A função de retorno de chamada `FunctionLeave3` notifica o criador de perfil conforme as funções estão sendo chamadas, mas não oferece suporte à inspeção de valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="ac043-108">The `FunctionLeave3` callback function notifies the profiler as functions are being called, but does not support return value inspection.</span></span> <span data-ttu-id="ac043-109">Use o [método ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) para registrar sua implementação dessa função.</span><span class="sxs-lookup"><span data-stu-id="ac043-109">Use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="ac043-110">A função `FunctionLeave3` é um retorno de chamada; Você deve implementá-lo.</span><span class="sxs-lookup"><span data-stu-id="ac043-110">The `FunctionLeave3` function is a callback; you must implement it.</span></span> <span data-ttu-id="ac043-111">A implementação deve usar o `__declspec(naked)` atributo de classe de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="ac043-111">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="ac043-112">O mecanismo de execução não salva nenhum registro antes de chamar essa função.</span><span class="sxs-lookup"><span data-stu-id="ac043-112">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="ac043-113">Na entrada, você deve salvar todos os registros que usar, incluindo aqueles na FPU (unidade de ponto flutuante).</span><span class="sxs-lookup"><span data-stu-id="ac043-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="ac043-114">Ao sair, você deve restaurar a pilha removendo todos os parâmetros que foram enviados por Push por seu chamador.</span><span class="sxs-lookup"><span data-stu-id="ac043-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="ac043-115">A implementação de `FunctionLeave3` não deve bloquear, pois atrasará a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="ac043-115">The implementation of `FunctionLeave3` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="ac043-116">A implementação não deve tentar uma coleta de lixo, pois a pilha pode não estar em um estado amigável de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="ac043-116">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="ac043-117">Se uma coleta de lixo for tentada, o tempo de execução será bloqueado até que `FunctionLeave3` retorne.</span><span class="sxs-lookup"><span data-stu-id="ac043-117">If a garbage collection is attempted, the runtime will block until `FunctionLeave3` returns.</span></span>  
  
 <span data-ttu-id="ac043-118">A função `FunctionLeave3` não deve chamar um código gerenciado ou causar uma alocação de memória gerenciada de qualquer forma.</span><span class="sxs-lookup"><span data-stu-id="ac043-118">The `FunctionLeave3` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac043-119">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="ac043-119">Requirements</span></span>  
 <span data-ttu-id="ac043-120">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac043-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac043-121">**Cabeçalho:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="ac043-121">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="ac043-122">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ac043-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ac043-123">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac043-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac043-124">Veja também</span><span class="sxs-lookup"><span data-stu-id="ac043-124">See also</span></span>

- [<span data-ttu-id="ac043-125">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="ac043-125">FunctionEnter3</span></span>](functionenter3-function.md)
- [<span data-ttu-id="ac043-126">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="ac043-126">FunctionTailcall3</span></span>](functiontailcall3-function.md)
- [<span data-ttu-id="ac043-127">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="ac043-127">FunctionEnter3WithInfo</span></span>](functiontailcall3-function.md)
- [<span data-ttu-id="ac043-128">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="ac043-128">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="ac043-129">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="ac043-129">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="ac043-130">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="ac043-130">SetEnterLeaveFunctionHooks3</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="ac043-131">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="ac043-131">SetEnterLeaveFunctionHooks3WithInfo</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="ac043-132">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="ac043-132">SetFunctionIDMapper</span></span>](icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="ac043-133">SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="ac043-133">SetFunctionIDMapper2</span></span>](icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="ac043-134">Criando perfil de funções estáticas globais</span><span class="sxs-lookup"><span data-stu-id="ac043-134">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
