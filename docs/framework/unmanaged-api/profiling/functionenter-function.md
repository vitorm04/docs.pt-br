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
ms.openlocfilehash: ad34592223433f0bf541c390674bcf96839b6ca8
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440823"
---
# <a name="functionenter-function"></a><span data-ttu-id="65ef5-102">Função FunctionEnter</span><span class="sxs-lookup"><span data-stu-id="65ef5-102">FunctionEnter Function</span></span>
<span data-ttu-id="65ef5-103">Notifica o criador de perfil que o controle está sendo passado para uma função.</span><span class="sxs-lookup"><span data-stu-id="65ef5-103">Notifies the profiler that control is being passed to a function.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="65ef5-104">A função `FunctionEnter` foi preterida no .NET Framework versão 2,0, e seu uso incorrerá em uma penalidade de desempenho.</span><span class="sxs-lookup"><span data-stu-id="65ef5-104">The `FunctionEnter` function is deprecated in the .NET Framework version 2.0, and its use will incur a performance penalty.</span></span> <span data-ttu-id="65ef5-105">Em vez disso, use a função [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) .</span><span class="sxs-lookup"><span data-stu-id="65ef5-105">Use the [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65ef5-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="65ef5-106">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionEnter (  
    [in]  FunctionID funcID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="65ef5-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="65ef5-107">Parameters</span></span>  
 `funcID`  
 <span data-ttu-id="65ef5-108">no O identificador da função à qual o controle é passado.</span><span class="sxs-lookup"><span data-stu-id="65ef5-108">[in] The identifier of the function to which control is passed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="65ef5-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="65ef5-109">Remarks</span></span>  
 <span data-ttu-id="65ef5-110">A função `FunctionEnter` é um retorno de chamada; Você deve implementá-lo.</span><span class="sxs-lookup"><span data-stu-id="65ef5-110">The `FunctionEnter` function is a callback; you must implement it.</span></span> <span data-ttu-id="65ef5-111">A implementação deve usar o atributo de classe de armazenamento `__declspec`(`naked`).</span><span class="sxs-lookup"><span data-stu-id="65ef5-111">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="65ef5-112">O mecanismo de execução não salva nenhum registro antes de chamar essa função.</span><span class="sxs-lookup"><span data-stu-id="65ef5-112">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="65ef5-113">Na entrada, você deve salvar todos os registros que usar, incluindo aqueles na FPU (unidade de ponto flutuante).</span><span class="sxs-lookup"><span data-stu-id="65ef5-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="65ef5-114">Ao sair, você deve restaurar a pilha removendo todos os parâmetros que foram enviados por Push por seu chamador.</span><span class="sxs-lookup"><span data-stu-id="65ef5-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="65ef5-115">A implementação de `FunctionEnter` não deve bloquear, pois atrasará a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="65ef5-115">The implementation of `FunctionEnter` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="65ef5-116">A implementação não deve tentar uma coleta de lixo porque a pilha pode não estar em um estado amigável de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="65ef5-116">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="65ef5-117">Se uma coleta de lixo for tentada, o tempo de execução será bloqueado até que `FunctionEnter` retorne.</span><span class="sxs-lookup"><span data-stu-id="65ef5-117">If a garbage collection is attempted, the runtime will block until `FunctionEnter` returns.</span></span>  
  
 <span data-ttu-id="65ef5-118">Além disso, a função `FunctionEnter` não deve chamar um código gerenciado ou, de qualquer forma, causar uma alocação de memória gerenciada.</span><span class="sxs-lookup"><span data-stu-id="65ef5-118">Also, the `FunctionEnter` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65ef5-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="65ef5-119">Requirements</span></span>  
 <span data-ttu-id="65ef5-120">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65ef5-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65ef5-121">**Cabeçalho:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="65ef5-121">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="65ef5-122">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="65ef5-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="65ef5-123">**Versões do .NET Framework:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="65ef5-123">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65ef5-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="65ef5-124">See also</span></span>

- [<span data-ttu-id="65ef5-125">Função FunctionEnter2</span><span class="sxs-lookup"><span data-stu-id="65ef5-125">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [<span data-ttu-id="65ef5-126">Função FunctionLeave2</span><span class="sxs-lookup"><span data-stu-id="65ef5-126">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [<span data-ttu-id="65ef5-127">Função FunctionTailcall2</span><span class="sxs-lookup"><span data-stu-id="65ef5-127">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)
- [<span data-ttu-id="65ef5-128">Método SetEnterLeaveFunctionHooks2</span><span class="sxs-lookup"><span data-stu-id="65ef5-128">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="65ef5-129">Criando perfil de funções estáticas globais</span><span class="sxs-lookup"><span data-stu-id="65ef5-129">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
