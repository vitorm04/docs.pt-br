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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 238a5f19bd8cbd89a5537b2b9297bfa9e1f54613
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952882"
---
# <a name="functionleave-function"></a><span data-ttu-id="bffd6-102">Função FunctionLeave</span><span class="sxs-lookup"><span data-stu-id="bffd6-102">FunctionLeave Function</span></span>
<span data-ttu-id="bffd6-103">Notifica o criador de perfil de que uma função está prestes a retornar ao chamador.</span><span class="sxs-lookup"><span data-stu-id="bffd6-103">Notifies the profiler that a function is about to return to the caller.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bffd6-104">A `FunctionLeave` função foi preterida no .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="bffd6-104">The `FunctionLeave` function is deprecated in the .NET Framework 2.0.</span></span> <span data-ttu-id="bffd6-105">Ele continuará funcionando, mas incorrerá em uma penalidade de desempenho.</span><span class="sxs-lookup"><span data-stu-id="bffd6-105">It will continue to work, but will incur a performance penalty.</span></span> <span data-ttu-id="bffd6-106">Em vez disso, use a função [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) .</span><span class="sxs-lookup"><span data-stu-id="bffd6-106">Use the [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bffd6-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bffd6-107">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionLeave (  
    [in] FunctionID funcID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bffd6-108">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bffd6-108">Parameters</span></span>  
 `funcID`  
 <span data-ttu-id="bffd6-109">no O identificador da função que está retornando.</span><span class="sxs-lookup"><span data-stu-id="bffd6-109">[in] The identifier of the function that is returning.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bffd6-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="bffd6-110">Remarks</span></span>  
 <span data-ttu-id="bffd6-111">A `FunctionLeave` função é um retorno de chamada; você deve implementá-la.</span><span class="sxs-lookup"><span data-stu-id="bffd6-111">The `FunctionLeave` function is a callback; you must implement it.</span></span> <span data-ttu-id="bffd6-112">A implementação deve usar o `__declspec`atributo`naked`de classe de armazenamento ().</span><span class="sxs-lookup"><span data-stu-id="bffd6-112">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="bffd6-113">O mecanismo de execução não salva nenhum registro antes de chamar essa função.</span><span class="sxs-lookup"><span data-stu-id="bffd6-113">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="bffd6-114">Na entrada, você deve salvar todos os registros que usar, incluindo aqueles na FPU (unidade de ponto flutuante).</span><span class="sxs-lookup"><span data-stu-id="bffd6-114">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="bffd6-115">Ao sair, você deve restaurar a pilha removendo todos os parâmetros que foram enviados por Push por seu chamador.</span><span class="sxs-lookup"><span data-stu-id="bffd6-115">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="bffd6-116">A implementação de `FunctionLeave` não deve bloquear, pois atrasará a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="bffd6-116">The implementation of `FunctionLeave` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="bffd6-117">A implementação não deve tentar uma coleta de lixo porque a pilha pode não estar em um estado amigável de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="bffd6-117">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="bffd6-118">Se for feita uma tentativa de coleta de lixo, o tempo de `FunctionLeave` execução será bloqueado até o retorno.</span><span class="sxs-lookup"><span data-stu-id="bffd6-118">If a garbage collection is attempted, the runtime will block until `FunctionLeave` returns.</span></span>  
  
 <span data-ttu-id="bffd6-119">Além disso, `FunctionLeave` a função não deve chamar um código gerenciado ou, de qualquer forma, causar uma alocação de memória gerenciada.</span><span class="sxs-lookup"><span data-stu-id="bffd6-119">Also, the `FunctionLeave` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bffd6-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bffd6-120">Requirements</span></span>  
 <span data-ttu-id="bffd6-121">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bffd6-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bffd6-122">**Cabeçalho:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="bffd6-122">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="bffd6-123">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bffd6-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bffd6-124">**.NET Framework versões:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="bffd6-124">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bffd6-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bffd6-125">See also</span></span>

- [<span data-ttu-id="bffd6-126">Função FunctionEnter2</span><span class="sxs-lookup"><span data-stu-id="bffd6-126">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [<span data-ttu-id="bffd6-127">Função FunctionLeave2</span><span class="sxs-lookup"><span data-stu-id="bffd6-127">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [<span data-ttu-id="bffd6-128">Função FunctionTailcall2</span><span class="sxs-lookup"><span data-stu-id="bffd6-128">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)
- [<span data-ttu-id="bffd6-129">Método SetEnterLeaveFunctionHooks2</span><span class="sxs-lookup"><span data-stu-id="bffd6-129">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="bffd6-130">Criando perfil de funções estáticas globais</span><span class="sxs-lookup"><span data-stu-id="bffd6-130">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
