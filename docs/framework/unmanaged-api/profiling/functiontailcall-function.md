---
title: Função FunctionTailcall
ms.date: 03/30/2017
api_name:
- FunctionTailcall
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall
helpviewer_keywords:
- FunctionTailcall function [.NET Framework profiling]
ms.assetid: 66347e03-9a97-41e8-8f9d-89b80803f7b5
topic_type:
- apiref
ms.openlocfilehash: 42ea497bdcab71518bec08514b827d76f0317d57
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500592"
---
# <a name="functiontailcall-function"></a><span data-ttu-id="8c5f4-102">Função FunctionTailcall</span><span class="sxs-lookup"><span data-stu-id="8c5f4-102">FunctionTailcall Function</span></span>
<span data-ttu-id="8c5f4-103">Notifica o criador de perfil de que a função atualmente em execução está prestes a executar uma chamada tail para outra função.</span><span class="sxs-lookup"><span data-stu-id="8c5f4-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8c5f4-104">A `FunctionTailcall` função foi preterida na versão .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="8c5f4-104">The `FunctionTailcall` function is deprecated in the .NET Framework version 2.0.</span></span> <span data-ttu-id="8c5f4-105">Ele continuará funcionando, mas incorrerá em uma penalidade de desempenho.</span><span class="sxs-lookup"><span data-stu-id="8c5f4-105">It will continue to work, but will incur a performance penalty.</span></span> <span data-ttu-id="8c5f4-106">Em vez disso, use a função [FunctionTailcall2](functiontailcall2-function.md) .</span><span class="sxs-lookup"><span data-stu-id="8c5f4-106">Use the [FunctionTailcall2](functiontailcall2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c5f4-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8c5f4-107">Syntax</span></span>  
  
```cpp
void __stdcall FunctionTailcall (  
    [in] FunctionID funcID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8c5f4-108">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8c5f4-108">Parameters</span></span>

- `funcID`

  <span data-ttu-id="8c5f4-109">\[in] o identificador da função atualmente em execução que está prestes a fazer uma chamada tail.</span><span class="sxs-lookup"><span data-stu-id="8c5f4-109">\[in] The identifier of the currently executing function that is about to make a tail call.</span></span>

## <a name="remarks"></a><span data-ttu-id="8c5f4-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="8c5f4-110">Remarks</span></span>  
 <span data-ttu-id="8c5f4-111">A função de destino da chamada tail usará o quadro de pilhas atual e retornará diretamente para o chamador da função que fez a chamada final.</span><span class="sxs-lookup"><span data-stu-id="8c5f4-111">The target function of the tail call will use the current stack frame, and will return directly to the caller of the function that made the tail call.</span></span> <span data-ttu-id="8c5f4-112">Isso significa que um retorno de chamada [FunctionLeave](functionleave-function.md) não será emitido para uma função que seja o destino de uma chamada tail.</span><span class="sxs-lookup"><span data-stu-id="8c5f4-112">This means that a [FunctionLeave](functionleave-function.md) callback will not be issued for a function that is the target of a tail call.</span></span>  
  
 <span data-ttu-id="8c5f4-113">A `FunctionTailcall` função é um retorno de chamada; você deve implementá-la.</span><span class="sxs-lookup"><span data-stu-id="8c5f4-113">The `FunctionTailcall` function is a callback; you must implement it.</span></span> <span data-ttu-id="8c5f4-114">A implementação deve usar o `__declspec` `naked` atributo de classe de armazenamento ().</span><span class="sxs-lookup"><span data-stu-id="8c5f4-114">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="8c5f4-115">O mecanismo de execução não salva nenhum registro antes de chamar essa função.</span><span class="sxs-lookup"><span data-stu-id="8c5f4-115">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="8c5f4-116">Na entrada, você deve salvar todos os registros que usar, incluindo aqueles na FPU (unidade de ponto flutuante).</span><span class="sxs-lookup"><span data-stu-id="8c5f4-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="8c5f4-117">Ao sair, você deve restaurar a pilha removendo todos os parâmetros que foram enviados por Push por seu chamador.</span><span class="sxs-lookup"><span data-stu-id="8c5f4-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="8c5f4-118">A implementação de `FunctionTailcall` não deve bloquear, pois atrasará a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="8c5f4-118">The implementation of `FunctionTailcall` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="8c5f4-119">A implementação não deve tentar uma coleta de lixo porque a pilha pode não estar em um estado amigável de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="8c5f4-119">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="8c5f4-120">Se for feita uma tentativa de coleta de lixo, o tempo de execução será bloqueado até o `FunctionTailcall` retorno.</span><span class="sxs-lookup"><span data-stu-id="8c5f4-120">If a garbage collection is attempted, the runtime will block until `FunctionTailcall` returns.</span></span>  
  
 <span data-ttu-id="8c5f4-121">Além disso, a `FunctionTailcall` função não deve chamar um código gerenciado ou, de qualquer forma, causar uma alocação de memória gerenciada.</span><span class="sxs-lookup"><span data-stu-id="8c5f4-121">Also, the `FunctionTailcall` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c5f4-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8c5f4-122">Requirements</span></span>  
 <span data-ttu-id="8c5f4-123">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c5f4-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c5f4-124">**Cabeçalho:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="8c5f4-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="8c5f4-125">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8c5f4-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8c5f4-126">**Versões do .NET Framework:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="8c5f4-126">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c5f4-127">Confira também</span><span class="sxs-lookup"><span data-stu-id="8c5f4-127">See also</span></span>

- [<span data-ttu-id="8c5f4-128">Função FunctionEnter2</span><span class="sxs-lookup"><span data-stu-id="8c5f4-128">FunctionEnter2 Function</span></span>](functionenter2-function.md)
- [<span data-ttu-id="8c5f4-129">Função FunctionLeave2</span><span class="sxs-lookup"><span data-stu-id="8c5f4-129">FunctionLeave2 Function</span></span>](functionleave2-function.md)
- [<span data-ttu-id="8c5f4-130">Método SetEnterLeaveFunctionHooks2</span><span class="sxs-lookup"><span data-stu-id="8c5f4-130">SetEnterLeaveFunctionHooks2 Method</span></span>](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="8c5f4-131">Criando perfil de funções estáticas globais</span><span class="sxs-lookup"><span data-stu-id="8c5f4-131">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
