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
ms.openlocfilehash: 2d99c6d8bd2af02456c6a90143b524c337483868
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866876"
---
# <a name="functiontailcall2-function"></a><span data-ttu-id="23732-102">Função FunctionTailcall2</span><span class="sxs-lookup"><span data-stu-id="23732-102">FunctionTailcall2 Function</span></span>
<span data-ttu-id="23732-103">Notifica o criador de perfil de que a função atualmente em execução está prestes a executar uma chamada tail para outra função e fornece informações sobre o registro de ativação.</span><span class="sxs-lookup"><span data-stu-id="23732-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function and provides information about the stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23732-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="23732-104">Syntax</span></span>  
  
```cpp
void __stdcall FunctionTailcall2 (  
    [in] FunctionID         funcId,   
    [in] UINT_PTR           clientData,   
    [in] COR_PRF_FRAME_INFO func  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="23732-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="23732-105">Parameters</span></span>

- `funcId`

  <span data-ttu-id="23732-106">\[em] o identificador da função atualmente em execução que está prestes a fazer uma chamada final.</span><span class="sxs-lookup"><span data-stu-id="23732-106">\[in] The identifier of the currently executing function that is about to make a tail call.</span></span>

- `clientData`

  <span data-ttu-id="23732-107">\[in] o identificador da função remapeada, que o criador de perfil especificou anteriormente via [FunctionIDMapper](functionidmapper-function.md), da função atualmente em execução que está prestes a fazer uma chamada final.</span><span class="sxs-lookup"><span data-stu-id="23732-107">\[in] The remapped function identifier, which the profiler previously specified via [FunctionIDMapper](functionidmapper-function.md), of the currently executing function that is about to make a tail call.</span></span>
  
- `func`

  <span data-ttu-id="23732-108">\[em] um valor de `COR_PRF_FRAME_INFO` que aponta para informações sobre o registro de ativação.</span><span class="sxs-lookup"><span data-stu-id="23732-108">\[in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>

  <span data-ttu-id="23732-109">O criador de perfil deve tratar isso como um identificador opaco que pode ser passado de volta para o mecanismo de execução no método [ICorProfilerInfo2:: GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="23732-109">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>

## <a name="remarks"></a><span data-ttu-id="23732-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="23732-110">Remarks</span></span>  
 <span data-ttu-id="23732-111">A função de destino da chamada tail usará o quadro de pilhas atual e retornará diretamente para o chamador da função que fez a chamada final.</span><span class="sxs-lookup"><span data-stu-id="23732-111">The target function of the tail call will use the current stack frame, and will return directly to the caller of the function that made the tail call.</span></span> <span data-ttu-id="23732-112">Isso significa que um retorno de chamada [FunctionLeave2](functionleave2-function.md) não será emitido para uma função que seja o destino de uma chamada tail.</span><span class="sxs-lookup"><span data-stu-id="23732-112">This means that a [FunctionLeave2](functionleave2-function.md) callback will not be issued for a function that is the target of a tail call.</span></span>  
  
 <span data-ttu-id="23732-113">O valor do parâmetro `func` não é válido depois que a função `FunctionTailcall2` retorna, pois o valor pode ser alterado ou destruído.</span><span class="sxs-lookup"><span data-stu-id="23732-113">The value of the `func` parameter is not valid after the `FunctionTailcall2` function returns because the value may change or be destroyed.</span></span>  
  
 <span data-ttu-id="23732-114">A função `FunctionTailcall2` é um retorno de chamada; Você deve implementá-lo.</span><span class="sxs-lookup"><span data-stu-id="23732-114">The `FunctionTailcall2` function is a callback; you must implement it.</span></span> <span data-ttu-id="23732-115">A implementação deve usar o atributo de classe de armazenamento `__declspec`(`naked`).</span><span class="sxs-lookup"><span data-stu-id="23732-115">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="23732-116">O mecanismo de execução não salva nenhum registro antes de chamar essa função.</span><span class="sxs-lookup"><span data-stu-id="23732-116">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="23732-117">Na entrada, você deve salvar todos os registros que usar, incluindo aqueles na FPU (unidade de ponto flutuante).</span><span class="sxs-lookup"><span data-stu-id="23732-117">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="23732-118">Ao sair, você deve restaurar a pilha removendo todos os parâmetros que foram enviados por Push por seu chamador.</span><span class="sxs-lookup"><span data-stu-id="23732-118">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="23732-119">A implementação de `FunctionTailcall2` não deve bloquear, pois atrasará a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="23732-119">The implementation of `FunctionTailcall2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="23732-120">A implementação não deve tentar uma coleta de lixo porque a pilha pode não estar em um estado amigável de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="23732-120">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="23732-121">Se uma coleta de lixo for tentada, o tempo de execução será bloqueado até que `FunctionTailcall2` retorne.</span><span class="sxs-lookup"><span data-stu-id="23732-121">If a garbage collection is attempted, the runtime will block until `FunctionTailcall2` returns.</span></span>  
  
 <span data-ttu-id="23732-122">Além disso, a função `FunctionTailcall2` não deve chamar um código gerenciado ou, de qualquer forma, causar uma alocação de memória gerenciada.</span><span class="sxs-lookup"><span data-stu-id="23732-122">Also, the `FunctionTailcall2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23732-123">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="23732-123">Requirements</span></span>  
 <span data-ttu-id="23732-124">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="23732-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23732-125">**Cabeçalho:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="23732-125">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="23732-126">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="23732-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="23732-127">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23732-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23732-128">Veja também</span><span class="sxs-lookup"><span data-stu-id="23732-128">See also</span></span>

- [<span data-ttu-id="23732-129">Função FunctionEnter2</span><span class="sxs-lookup"><span data-stu-id="23732-129">FunctionEnter2 Function</span></span>](functionenter2-function.md)
- [<span data-ttu-id="23732-130">Função FunctionLeave2</span><span class="sxs-lookup"><span data-stu-id="23732-130">FunctionLeave2 Function</span></span>](functionleave2-function.md)
- [<span data-ttu-id="23732-131">Método SetEnterLeaveFunctionHooks2</span><span class="sxs-lookup"><span data-stu-id="23732-131">SetEnterLeaveFunctionHooks2 Method</span></span>](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="23732-132">Criando perfil de funções estáticas globais</span><span class="sxs-lookup"><span data-stu-id="23732-132">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
