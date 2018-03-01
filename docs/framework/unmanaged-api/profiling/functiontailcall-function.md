---
title: "Função FunctionTailcall"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 223f112ba405e29b800456adca2f83e0cef6e7b8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="functiontailcall-function"></a><span data-ttu-id="38e6b-102">Função FunctionTailcall</span><span class="sxs-lookup"><span data-stu-id="38e6b-102">FunctionTailcall Function</span></span>
<span data-ttu-id="38e6b-103">Notifica o criador de perfil que a função atualmente em execução está prestes a realizar uma chamada tail para outra função.</span><span class="sxs-lookup"><span data-stu-id="38e6b-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="38e6b-104">O `FunctionTailcall` função está obsoleto no .NET Framework versão 2.0.</span><span class="sxs-lookup"><span data-stu-id="38e6b-104">The `FunctionTailcall` function is deprecated in the .NET Framework version 2.0.</span></span> <span data-ttu-id="38e6b-105">Ele continuará a funcionar, mas provocará uma penalidade de desempenho.</span><span class="sxs-lookup"><span data-stu-id="38e6b-105">It will continue to work, but will incur a performance penalty.</span></span> <span data-ttu-id="38e6b-106">Use o [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) function em vez disso.</span><span class="sxs-lookup"><span data-stu-id="38e6b-106">Use the [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38e6b-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="38e6b-107">Syntax</span></span>  
  
```  
void __stdcall FunctionTailcall (  
    [in] FunctionID funcID  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="38e6b-108">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="38e6b-108">Parameters</span></span>  
 `funcID`  
 <span data-ttu-id="38e6b-109">[in] O identificador da função atualmente em execução que está prestes a fazer uma cauda chamada.</span><span class="sxs-lookup"><span data-stu-id="38e6b-109">[in] The identifier of the currently executing function that is about to make a tail call.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="38e6b-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="38e6b-110">Remarks</span></span>  
 <span data-ttu-id="38e6b-111">A função de destino da chamada final usará o quadro de pilhas atual e retornará diretamente para o chamador da função que fez com que a parte final chamada.</span><span class="sxs-lookup"><span data-stu-id="38e6b-111">The target function of the tail call will use the current stack frame, and will return directly to the caller of the function that made the tail call.</span></span> <span data-ttu-id="38e6b-112">Isso significa que um [FunctionLeave](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md) retorno de chamada não será emitido para uma função que é o destino de uma chamada tail.</span><span class="sxs-lookup"><span data-stu-id="38e6b-112">This means that a [FunctionLeave](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md) callback will not be issued for a function that is the target of a tail call.</span></span>  
  
 <span data-ttu-id="38e6b-113">O `FunctionTailcall` função é um retorno de chamada; você deve implementá-la.</span><span class="sxs-lookup"><span data-stu-id="38e6b-113">The `FunctionTailcall` function is a callback; you must implement it.</span></span> <span data-ttu-id="38e6b-114">A implementação deve usar o `__declspec`(`naked`) atributo de classe de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="38e6b-114">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="38e6b-115">O mecanismo de execução não salva quaisquer registros antes de chamar essa função.</span><span class="sxs-lookup"><span data-stu-id="38e6b-115">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="38e6b-116">Na entrada, você deve salvar todos os registros que você usa, incluindo aqueles na unidade de ponto flutuante (FPU).</span><span class="sxs-lookup"><span data-stu-id="38e6b-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="38e6b-117">Na saída, você deve restaurar a pilha por retirar desativar todos os parâmetros que foram empurrados pelo chamador.</span><span class="sxs-lookup"><span data-stu-id="38e6b-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="38e6b-118">A implementação de `FunctionTailcall` não devem bloquear porque ele atrasará a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="38e6b-118">The implementation of `FunctionTailcall` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="38e6b-119">A implementação não deve tentar uma coleta de lixo, porque a pilha pode não estar em um estado de amigável para coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="38e6b-119">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="38e6b-120">Se você tentar uma coleta de lixo, tempo de execução será bloqueado até que `FunctionTailcall` retorna.</span><span class="sxs-lookup"><span data-stu-id="38e6b-120">If a garbage collection is attempted, the runtime will block until `FunctionTailcall` returns.</span></span>  
  
 <span data-ttu-id="38e6b-121">Além disso, o `FunctionTailcall` função não deve chamar código gerenciado ou em qualquer causa de maneira uma alocação de memória gerenciada.</span><span class="sxs-lookup"><span data-stu-id="38e6b-121">Also, the `FunctionTailcall` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38e6b-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="38e6b-122">Requirements</span></span>  
 <span data-ttu-id="38e6b-123">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38e6b-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38e6b-124">**Cabeçalho:** Corprof. idl</span><span class="sxs-lookup"><span data-stu-id="38e6b-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="38e6b-125">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="38e6b-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="38e6b-126">**Versões do .NET framework:** 1.1 e 1.0</span><span class="sxs-lookup"><span data-stu-id="38e6b-126">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38e6b-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="38e6b-127">See Also</span></span>  
 [<span data-ttu-id="38e6b-128">Função FunctionEnter2</span><span class="sxs-lookup"><span data-stu-id="38e6b-128">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 [<span data-ttu-id="38e6b-129">Função FunctionLeave2</span><span class="sxs-lookup"><span data-stu-id="38e6b-129">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 [<span data-ttu-id="38e6b-130">Método SetEnterLeaveFunctionHooks2</span><span class="sxs-lookup"><span data-stu-id="38e6b-130">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)  
 [<span data-ttu-id="38e6b-131">Criando perfil de funções estáticas globais</span><span class="sxs-lookup"><span data-stu-id="38e6b-131">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
