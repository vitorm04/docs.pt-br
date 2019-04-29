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
ms.openlocfilehash: e6018b5b06a138b38b7b97df280a3e4c4ea0512d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61598955"
---
# <a name="functionenter-function"></a><span data-ttu-id="380eb-102">Função FunctionEnter</span><span class="sxs-lookup"><span data-stu-id="380eb-102">FunctionEnter Function</span></span>
<span data-ttu-id="380eb-103">Notifica o criador de perfil que o controle está sendo passado para uma função.</span><span class="sxs-lookup"><span data-stu-id="380eb-103">Notifies the profiler that control is being passed to a function.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="380eb-104">O `FunctionEnter` função foi preterida no .NET Framework versão 2.0, e seu uso provocará uma penalidade de desempenho.</span><span class="sxs-lookup"><span data-stu-id="380eb-104">The `FunctionEnter` function is deprecated in the .NET Framework version 2.0, and its use will incur a performance penalty.</span></span> <span data-ttu-id="380eb-105">Use o [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) function em vez disso.</span><span class="sxs-lookup"><span data-stu-id="380eb-105">Use the [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="380eb-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="380eb-106">Syntax</span></span>  
  
```  
void __stdcall FunctionEnter (  
    [in]  FunctionID funcID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="380eb-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="380eb-107">Parameters</span></span>  
 `funcID`  
 <span data-ttu-id="380eb-108">[in] O identificador da função à qual o controle é passado.</span><span class="sxs-lookup"><span data-stu-id="380eb-108">[in] The identifier of the function to which control is passed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="380eb-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="380eb-109">Remarks</span></span>  
 <span data-ttu-id="380eb-110">O `FunctionEnter` função é um retorno de chamada; você deve implementá-la.</span><span class="sxs-lookup"><span data-stu-id="380eb-110">The `FunctionEnter` function is a callback; you must implement it.</span></span> <span data-ttu-id="380eb-111">A implementação deve usar o `__declspec`(`naked`) atributo de classe de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="380eb-111">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="380eb-112">O mecanismo de execução não salva qualquer registros antes de chamar essa função.</span><span class="sxs-lookup"><span data-stu-id="380eb-112">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="380eb-113">Na entrada, você deve salvar todos os registros que você usa, incluindo aqueles na unidade de ponto flutuante (FPU).</span><span class="sxs-lookup"><span data-stu-id="380eb-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="380eb-114">Na saída, você deve restaurar a pilha de popping desativar todos os parâmetros que foram enviados por push ao seu chamador.</span><span class="sxs-lookup"><span data-stu-id="380eb-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="380eb-115">A implementação de `FunctionEnter` não devem bloquear porque isso atrasará a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="380eb-115">The implementation of `FunctionEnter` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="380eb-116">A implementação não deve tentar uma coleta de lixo, porque a pilha não pode estar em um estado de amigável para coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="380eb-116">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="380eb-117">Se você tentar uma coleta de lixo, o tempo de execução será bloqueado até que `FunctionEnter` retorna.</span><span class="sxs-lookup"><span data-stu-id="380eb-117">If a garbage collection is attempted, the runtime will block until `FunctionEnter` returns.</span></span>  
  
 <span data-ttu-id="380eb-118">Além disso, o `FunctionEnter` função não deve chamar código gerenciado ou em qualquer causa de maneira uma alocação de memória gerenciada.</span><span class="sxs-lookup"><span data-stu-id="380eb-118">Also, the `FunctionEnter` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="380eb-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="380eb-119">Requirements</span></span>  
 <span data-ttu-id="380eb-120">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="380eb-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="380eb-121">**Cabeçalho:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="380eb-121">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="380eb-122">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="380eb-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="380eb-123">**Versões do .NET framework:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="380eb-123">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="380eb-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="380eb-124">See also</span></span>

- [<span data-ttu-id="380eb-125">Função FunctionEnter2</span><span class="sxs-lookup"><span data-stu-id="380eb-125">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [<span data-ttu-id="380eb-126">Função FunctionLeave2</span><span class="sxs-lookup"><span data-stu-id="380eb-126">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [<span data-ttu-id="380eb-127">Função FunctionTailcall2</span><span class="sxs-lookup"><span data-stu-id="380eb-127">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)
- [<span data-ttu-id="380eb-128">Método SetEnterLeaveFunctionHooks2</span><span class="sxs-lookup"><span data-stu-id="380eb-128">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="380eb-129">Criando perfil de funções estáticas globais</span><span class="sxs-lookup"><span data-stu-id="380eb-129">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
