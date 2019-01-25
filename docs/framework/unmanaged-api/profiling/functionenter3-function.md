---
title: Função FunctionEnter3
ms.date: 03/30/2017
api_name:
- FunctionEnter3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionEnter3
helpviewer_keywords:
- FunctionEnter3 function [.NET Framework profiling]
ms.assetid: ef782c53-dae7-4990-b4ad-fddb1e690d4e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 08333c49d135b85d068df3a199aca15d74e78c46
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54619526"
---
# <a name="functionenter3-function"></a><span data-ttu-id="a38e1-102">Função FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="a38e1-102">FunctionEnter3 Function</span></span>
<span data-ttu-id="a38e1-103">Notifica o criador de perfil que o controle está sendo passado para uma função.</span><span class="sxs-lookup"><span data-stu-id="a38e1-103">Notifies the profiler that control is being passed to a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a38e1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a38e1-104">Syntax</span></span>  
  
```  
void __stdcall FunctionEnter3(FunctionOrRemappedID functionOrRemappedID);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a38e1-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a38e1-105">Parameters</span></span>  
 `functionOrRemappedID`  
 <span data-ttu-id="a38e1-106">[in] O identificador da função à qual o controle é passado.</span><span class="sxs-lookup"><span data-stu-id="a38e1-106">[in] The identifier of the function to which control is passed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a38e1-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="a38e1-107">Remarks</span></span>  
 <span data-ttu-id="a38e1-108">O `FunctionEnter3` função de retorno de chamada notifica o criador de perfil como funções estão sendo chamadas, mas não a inspeção do argumento de suporte não.</span><span class="sxs-lookup"><span data-stu-id="a38e1-108">The `FunctionEnter3` callback function notifies the profiler as functions are being called, but does not support argument inspection.</span></span> <span data-ttu-id="a38e1-109">Use o [método ICorProfilerInfo3::SetEnterLeaveFunctionHooks3](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) para registrar sua implementação dessa função.</span><span class="sxs-lookup"><span data-stu-id="a38e1-109">Use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="a38e1-110">O `FunctionEnter3` função é um retorno de chamada; você deve implementá-la.</span><span class="sxs-lookup"><span data-stu-id="a38e1-110">The `FunctionEnter3` function is a callback; you must implement it.</span></span> <span data-ttu-id="a38e1-111">A implementação deve usar o `__declspec(naked)` atributo de classe de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="a38e1-111">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="a38e1-112">O mecanismo de execução não salva qualquer registros antes de chamar essa função.</span><span class="sxs-lookup"><span data-stu-id="a38e1-112">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="a38e1-113">Na entrada, você deve salvar todos os registros que você usa, incluindo aqueles na unidade de ponto flutuante (FPU).</span><span class="sxs-lookup"><span data-stu-id="a38e1-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="a38e1-114">Na saída, você deve restaurar a pilha de popping desativar todos os parâmetros que foram enviados por push ao seu chamador.</span><span class="sxs-lookup"><span data-stu-id="a38e1-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a38e1-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a38e1-115">Requirements</span></span>  
 <span data-ttu-id="a38e1-116">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a38e1-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a38e1-117">**Cabeçalho:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="a38e1-117">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="a38e1-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a38e1-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a38e1-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a38e1-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a38e1-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a38e1-120">See also</span></span>
- [<span data-ttu-id="a38e1-121">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="a38e1-121">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)
- [<span data-ttu-id="a38e1-122">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="a38e1-122">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [<span data-ttu-id="a38e1-123">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="a38e1-123">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [<span data-ttu-id="a38e1-124">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="a38e1-124">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [<span data-ttu-id="a38e1-125">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="a38e1-125">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [<span data-ttu-id="a38e1-126">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="a38e1-126">SetEnterLeaveFunctionHooks3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="a38e1-127">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="a38e1-127">SetEnterLeaveFunctionHooks3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="a38e1-128">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="a38e1-128">SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="a38e1-129">SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="a38e1-129">SetFunctionIDMapper2</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="a38e1-130">Criando perfil de funções estáticas globais</span><span class="sxs-lookup"><span data-stu-id="a38e1-130">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
