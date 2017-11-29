---
title: "Função FunctionLeave"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: FunctionLeave
api_location: mscorwks.dll
api_type: COM
f1_keywords: FunctionLeave
helpviewer_keywords: FunctionLeave function [.NET Framework profiling]
ms.assetid: 18e89f45-e068-426a-be16-9f53a4346860
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3368a97adf6ffceaa5ac56b7ffe16d6e2802437c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="functionleave-function"></a><span data-ttu-id="8b97c-102">Função FunctionLeave</span><span class="sxs-lookup"><span data-stu-id="8b97c-102">FunctionLeave Function</span></span>
<span data-ttu-id="8b97c-103">Notifica o criador de perfil que uma função está prestes a retornar ao chamador.</span><span class="sxs-lookup"><span data-stu-id="8b97c-103">Notifies the profiler that a function is about to return to the caller.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8b97c-104">O `FunctionLeave` função está obsoleto no .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="8b97c-104">The `FunctionLeave` function is deprecated in the .NET Framework 2.0.</span></span> <span data-ttu-id="8b97c-105">Ele continuará a funcionar, mas provocará uma penalidade de desempenho.</span><span class="sxs-lookup"><span data-stu-id="8b97c-105">It will continue to work, but will incur a performance penalty.</span></span> <span data-ttu-id="8b97c-106">Use o [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) function em vez disso.</span><span class="sxs-lookup"><span data-stu-id="8b97c-106">Use the [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b97c-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8b97c-107">Syntax</span></span>  
  
```  
void __stdcall FunctionLeave (  
    [in] FunctionID funcID  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8b97c-108">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8b97c-108">Parameters</span></span>  
 `funcID`  
 <span data-ttu-id="8b97c-109">[in] O identificador da função que está retornando.</span><span class="sxs-lookup"><span data-stu-id="8b97c-109">[in] The identifier of the function that is returning.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8b97c-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="8b97c-110">Remarks</span></span>  
 <span data-ttu-id="8b97c-111">O `FunctionLeave` função é um retorno de chamada; você deve implementá-la.</span><span class="sxs-lookup"><span data-stu-id="8b97c-111">The `FunctionLeave` function is a callback; you must implement it.</span></span> <span data-ttu-id="8b97c-112">A implementação deve usar o `__declspec`(`naked`) atributo de classe de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="8b97c-112">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="8b97c-113">O mecanismo de execução não salva quaisquer registros antes de chamar essa função.</span><span class="sxs-lookup"><span data-stu-id="8b97c-113">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="8b97c-114">Na entrada, você deve salvar todos os registros que você usa, incluindo aqueles na unidade de ponto flutuante (FPU).</span><span class="sxs-lookup"><span data-stu-id="8b97c-114">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="8b97c-115">Na saída, você deve restaurar a pilha por retirar desativar todos os parâmetros que foram empurrados pelo chamador.</span><span class="sxs-lookup"><span data-stu-id="8b97c-115">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="8b97c-116">A implementação de `FunctionLeave` não devem bloquear porque ele atrasará a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="8b97c-116">The implementation of `FunctionLeave` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="8b97c-117">A implementação não deve tentar uma coleta de lixo, porque a pilha pode não estar em um estado de amigável para coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="8b97c-117">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="8b97c-118">Se você tentar uma coleta de lixo, tempo de execução será bloqueado até que `FunctionLeave` retorna.</span><span class="sxs-lookup"><span data-stu-id="8b97c-118">If a garbage collection is attempted, the runtime will block until `FunctionLeave` returns.</span></span>  
  
 <span data-ttu-id="8b97c-119">Além disso, o `FunctionLeave` função não deve chamar código gerenciado ou em qualquer causa de maneira uma alocação de memória gerenciada.</span><span class="sxs-lookup"><span data-stu-id="8b97c-119">Also, the `FunctionLeave` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b97c-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8b97c-120">Requirements</span></span>  
 <span data-ttu-id="8b97c-121">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b97c-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b97c-122">**Cabeçalho:** Corprof. idl</span><span class="sxs-lookup"><span data-stu-id="8b97c-122">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="8b97c-123">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8b97c-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8b97c-124">**Versões do .NET framework:** 1.1 e 1.0</span><span class="sxs-lookup"><span data-stu-id="8b97c-124">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b97c-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8b97c-125">See Also</span></span>  
 [<span data-ttu-id="8b97c-126">Função FunctionEnter2</span><span class="sxs-lookup"><span data-stu-id="8b97c-126">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 [<span data-ttu-id="8b97c-127">Função FunctionLeave2</span><span class="sxs-lookup"><span data-stu-id="8b97c-127">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 [<span data-ttu-id="8b97c-128">Função FunctionTailcall2</span><span class="sxs-lookup"><span data-stu-id="8b97c-128">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)  
 [<span data-ttu-id="8b97c-129">Método SetEnterLeaveFunctionHooks2</span><span class="sxs-lookup"><span data-stu-id="8b97c-129">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)  
 [<span data-ttu-id="8b97c-130">Funções estáticas globais de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="8b97c-130">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
