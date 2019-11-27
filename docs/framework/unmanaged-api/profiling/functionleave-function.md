---
title: Função FunctionLeave
ms.date: 03/30/2017
api_name:
- FunctionLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionLeave
helpviewer_keywords:
- FunctionLeave function [.NET Framework profiling]
ms.assetid: 18e89f45-e068-426a-be16-9f53a4346860
topic_type:
- apiref
ms.openlocfilehash: 774a5d4e48f00ea8c28977f3f685dcd5a8da3199
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440579"
---
# <a name="functionleave-function"></a><span data-ttu-id="b5c75-102">Função FunctionLeave</span><span class="sxs-lookup"><span data-stu-id="b5c75-102">FunctionLeave Function</span></span>
<span data-ttu-id="b5c75-103">Notifica o criador de perfil de que uma função está prestes a retornar ao chamador.</span><span class="sxs-lookup"><span data-stu-id="b5c75-103">Notifies the profiler that a function is about to return to the caller.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b5c75-104">A função `FunctionLeave` foi preterida no .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="b5c75-104">The `FunctionLeave` function is deprecated in the .NET Framework 2.0.</span></span> <span data-ttu-id="b5c75-105">Ele continuará funcionando, mas incorrerá em uma penalidade de desempenho.</span><span class="sxs-lookup"><span data-stu-id="b5c75-105">It will continue to work, but will incur a performance penalty.</span></span> <span data-ttu-id="b5c75-106">Em vez disso, use a função [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) .</span><span class="sxs-lookup"><span data-stu-id="b5c75-106">Use the [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5c75-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b5c75-107">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionLeave (  
    [in] FunctionID funcID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b5c75-108">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b5c75-108">Parameters</span></span>  
 `funcID`  
 <span data-ttu-id="b5c75-109">no O identificador da função que está retornando.</span><span class="sxs-lookup"><span data-stu-id="b5c75-109">[in] The identifier of the function that is returning.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b5c75-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="b5c75-110">Remarks</span></span>  
 <span data-ttu-id="b5c75-111">A função `FunctionLeave` é um retorno de chamada; Você deve implementá-lo.</span><span class="sxs-lookup"><span data-stu-id="b5c75-111">The `FunctionLeave` function is a callback; you must implement it.</span></span> <span data-ttu-id="b5c75-112">A implementação deve usar o atributo de classe de armazenamento `__declspec`(`naked`).</span><span class="sxs-lookup"><span data-stu-id="b5c75-112">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="b5c75-113">O mecanismo de execução não salva nenhum registro antes de chamar essa função.</span><span class="sxs-lookup"><span data-stu-id="b5c75-113">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="b5c75-114">Na entrada, você deve salvar todos os registros que usar, incluindo aqueles na FPU (unidade de ponto flutuante).</span><span class="sxs-lookup"><span data-stu-id="b5c75-114">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="b5c75-115">Ao sair, você deve restaurar a pilha removendo todos os parâmetros que foram enviados por Push por seu chamador.</span><span class="sxs-lookup"><span data-stu-id="b5c75-115">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="b5c75-116">A implementação de `FunctionLeave` não deve bloquear, pois atrasará a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="b5c75-116">The implementation of `FunctionLeave` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="b5c75-117">A implementação não deve tentar uma coleta de lixo porque a pilha pode não estar em um estado amigável de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="b5c75-117">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="b5c75-118">Se uma coleta de lixo for tentada, o tempo de execução será bloqueado até que `FunctionLeave` retorne.</span><span class="sxs-lookup"><span data-stu-id="b5c75-118">If a garbage collection is attempted, the runtime will block until `FunctionLeave` returns.</span></span>  
  
 <span data-ttu-id="b5c75-119">Além disso, a função `FunctionLeave` não deve chamar um código gerenciado ou, de qualquer forma, causar uma alocação de memória gerenciada.</span><span class="sxs-lookup"><span data-stu-id="b5c75-119">Also, the `FunctionLeave` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5c75-120">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="b5c75-120">Requirements</span></span>  
 <span data-ttu-id="b5c75-121">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b5c75-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5c75-122">**Cabeçalho:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="b5c75-122">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="b5c75-123">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b5c75-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b5c75-124">**Versões do .NET Framework:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="b5c75-124">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5c75-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b5c75-125">See also</span></span>

- [<span data-ttu-id="b5c75-126">Função FunctionEnter2</span><span class="sxs-lookup"><span data-stu-id="b5c75-126">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [<span data-ttu-id="b5c75-127">Função FunctionLeave2</span><span class="sxs-lookup"><span data-stu-id="b5c75-127">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [<span data-ttu-id="b5c75-128">Função FunctionTailcall2</span><span class="sxs-lookup"><span data-stu-id="b5c75-128">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)
- [<span data-ttu-id="b5c75-129">Método SetEnterLeaveFunctionHooks2</span><span class="sxs-lookup"><span data-stu-id="b5c75-129">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="b5c75-130">Criando perfil de funções estáticas globais</span><span class="sxs-lookup"><span data-stu-id="b5c75-130">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
