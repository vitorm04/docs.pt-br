---
title: Função FunctionEnter
ms.date: 03/30/2017
api_name:
- FunctionEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionEnter
helpviewer_keywords:
- FunctionEnter function [.NET Framework profiling]
ms.assetid: bf4ffa50-4506-4dd4-aa13-a0457b47ca74
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 77de59de8fcf3797237245ce42c7f0eaa96d3d24
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33451776"
---
# <a name="functionenter-function"></a><span data-ttu-id="4b39f-102">Função FunctionEnter</span><span class="sxs-lookup"><span data-stu-id="4b39f-102">FunctionEnter Function</span></span>
<span data-ttu-id="4b39f-103">Notifica o criador de perfil que o controle está sendo passado para uma função.</span><span class="sxs-lookup"><span data-stu-id="4b39f-103">Notifies the profiler that control is being passed to a function.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4b39f-104">O `FunctionEnter` função está obsoleto no .NET Framework versão 2.0, e seu uso provocará uma penalidade de desempenho.</span><span class="sxs-lookup"><span data-stu-id="4b39f-104">The `FunctionEnter` function is deprecated in the .NET Framework version 2.0, and its use will incur a performance penalty.</span></span> <span data-ttu-id="4b39f-105">Use o [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) function em vez disso.</span><span class="sxs-lookup"><span data-stu-id="4b39f-105">Use the [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b39f-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4b39f-106">Syntax</span></span>  
  
```  
void __stdcall FunctionEnter (  
    [in]  FunctionID funcID  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4b39f-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4b39f-107">Parameters</span></span>  
 `funcID`  
 <span data-ttu-id="4b39f-108">[in] O identificador da função à qual o controle é passado.</span><span class="sxs-lookup"><span data-stu-id="4b39f-108">[in] The identifier of the function to which control is passed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4b39f-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="4b39f-109">Remarks</span></span>  
 <span data-ttu-id="4b39f-110">O `FunctionEnter` função é um retorno de chamada; você deve implementá-la.</span><span class="sxs-lookup"><span data-stu-id="4b39f-110">The `FunctionEnter` function is a callback; you must implement it.</span></span> <span data-ttu-id="4b39f-111">A implementação deve usar o `__declspec`(`naked`) atributo de classe de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="4b39f-111">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="4b39f-112">O mecanismo de execução não salva quaisquer registros antes de chamar essa função.</span><span class="sxs-lookup"><span data-stu-id="4b39f-112">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="4b39f-113">Na entrada, você deve salvar todos os registros que você usa, incluindo aqueles na unidade de ponto flutuante (FPU).</span><span class="sxs-lookup"><span data-stu-id="4b39f-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="4b39f-114">Na saída, você deve restaurar a pilha por retirar desativar todos os parâmetros que foram empurrados pelo chamador.</span><span class="sxs-lookup"><span data-stu-id="4b39f-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="4b39f-115">A implementação de `FunctionEnter` não devem bloquear porque ele atrasará a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="4b39f-115">The implementation of `FunctionEnter` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="4b39f-116">A implementação não deve tentar uma coleta de lixo, porque a pilha pode não estar em um estado de amigável para coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="4b39f-116">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="4b39f-117">Se você tentar uma coleta de lixo, tempo de execução será bloqueado até que `FunctionEnter` retorna.</span><span class="sxs-lookup"><span data-stu-id="4b39f-117">If a garbage collection is attempted, the runtime will block until `FunctionEnter` returns.</span></span>  
  
 <span data-ttu-id="4b39f-118">Além disso, o `FunctionEnter` função não deve chamar código gerenciado ou em qualquer causa de maneira uma alocação de memória gerenciada.</span><span class="sxs-lookup"><span data-stu-id="4b39f-118">Also, the `FunctionEnter` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b39f-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4b39f-119">Requirements</span></span>  
 <span data-ttu-id="4b39f-120">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b39f-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b39f-121">**Cabeçalho:** Corprof. idl</span><span class="sxs-lookup"><span data-stu-id="4b39f-121">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="4b39f-122">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4b39f-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4b39f-123">**Versões do .NET framework:** 1.1 e 1.0</span><span class="sxs-lookup"><span data-stu-id="4b39f-123">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b39f-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4b39f-124">See Also</span></span>  
 [<span data-ttu-id="4b39f-125">Função FunctionEnter2</span><span class="sxs-lookup"><span data-stu-id="4b39f-125">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 [<span data-ttu-id="4b39f-126">Função FunctionLeave2</span><span class="sxs-lookup"><span data-stu-id="4b39f-126">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 [<span data-ttu-id="4b39f-127">Função FunctionTailcall2</span><span class="sxs-lookup"><span data-stu-id="4b39f-127">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)  
 [<span data-ttu-id="4b39f-128">Método SetEnterLeaveFunctionHooks2</span><span class="sxs-lookup"><span data-stu-id="4b39f-128">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)  
 [<span data-ttu-id="4b39f-129">Criando perfil de funções estáticas globais</span><span class="sxs-lookup"><span data-stu-id="4b39f-129">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
