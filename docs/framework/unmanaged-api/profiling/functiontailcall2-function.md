---
title: "Função FunctionTailcall2"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: FunctionTailcall2
api_location: mscorwks.dll
api_type: COM
f1_keywords: FunctionTailcall2
helpviewer_keywords: FunctionTailcall2 function [.NET Framework profiling]
ms.assetid: 249f9892-b5a9-41e1-b329-28a925904df6
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a9d6ccb08bc09bea2ec9e9a49333c92da8cb5695
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="functiontailcall2-function"></a><span data-ttu-id="bf40f-102">Função FunctionTailcall2</span><span class="sxs-lookup"><span data-stu-id="bf40f-102">FunctionTailcall2 Function</span></span>
<span data-ttu-id="bf40f-103">Notifica o criador de perfil que a função atualmente em execução está prestes a realizar uma chamada tail para outra função e fornece informações sobre o quadro de pilhas.</span><span class="sxs-lookup"><span data-stu-id="bf40f-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function and provides information about the stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf40f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bf40f-104">Syntax</span></span>  
  
```  
void __stdcall FunctionTailcall2 (  
    [in] FunctionID         funcId,   
    [in] UINT_PTR           clientData,   
    [in] COR_PRF_FRAME_INFO func  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bf40f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bf40f-105">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="bf40f-106">[in] O identificador da função atualmente em execução que está prestes a fazer uma cauda chamada.</span><span class="sxs-lookup"><span data-stu-id="bf40f-106">[in] The identifier of the currently executing function that is about to make a tail call.</span></span>  
  
 `clientData`  
 <span data-ttu-id="bf40f-107">[in] O identificador de função remapeados, o criador de perfil especificado anteriormente por meio de [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md), da função atualmente em execução que está prestes a fazer uma cauda chamada.</span><span class="sxs-lookup"><span data-stu-id="bf40f-107">[in] The remapped function identifier, which the profiler previously specified via [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md), of the currently executing function that is about to make a tail call.</span></span>  
  
 `func`  
 <span data-ttu-id="bf40f-108">[in] Um `COR_PRF_FRAME_INFO` valor que aponta para obter informações sobre o quadro de pilhas.</span><span class="sxs-lookup"><span data-stu-id="bf40f-108">[in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>  
  
 <span data-ttu-id="bf40f-109">O criador de perfil deve tratar isso como um identificador opaco que pode ser passado de volta para o mecanismo de execução no [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="bf40f-109">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bf40f-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="bf40f-110">Remarks</span></span>  
 <span data-ttu-id="bf40f-111">A função de destino da chamada final usará o quadro de pilhas atual e retornará diretamente para o chamador da função que fez com que a parte final chamada.</span><span class="sxs-lookup"><span data-stu-id="bf40f-111">The target function of the tail call will use the current stack frame, and will return directly to the caller of the function that made the tail call.</span></span> <span data-ttu-id="bf40f-112">Isso significa que um [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) retorno de chamada não será emitido para uma função que é o destino de uma chamada tail.</span><span class="sxs-lookup"><span data-stu-id="bf40f-112">This means that a [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) callback will not be issued for a function that is the target of a tail call.</span></span>  
  
 <span data-ttu-id="bf40f-113">O valor da `func` parâmetro não é válido após o `FunctionTailcall2` função retorna porque o valor pode ser alterado ou ser destruído.</span><span class="sxs-lookup"><span data-stu-id="bf40f-113">The value of the `func` parameter is not valid after the `FunctionTailcall2` function returns because the value may change or be destroyed.</span></span>  
  
 <span data-ttu-id="bf40f-114">O `FunctionTailcall2` função é um retorno de chamada; você deve implementá-la.</span><span class="sxs-lookup"><span data-stu-id="bf40f-114">The `FunctionTailcall2` function is a callback; you must implement it.</span></span> <span data-ttu-id="bf40f-115">A implementação deve usar o `__declspec`(`naked`) atributo de classe de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="bf40f-115">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="bf40f-116">O mecanismo de execução não salva quaisquer registros antes de chamar essa função.</span><span class="sxs-lookup"><span data-stu-id="bf40f-116">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="bf40f-117">Na entrada, você deve salvar todos os registros que você usa, incluindo aqueles na unidade de ponto flutuante (FPU).</span><span class="sxs-lookup"><span data-stu-id="bf40f-117">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="bf40f-118">Na saída, você deve restaurar a pilha por retirar desativar todos os parâmetros que foram empurrados pelo chamador.</span><span class="sxs-lookup"><span data-stu-id="bf40f-118">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="bf40f-119">A implementação de `FunctionTailcall2` não devem bloquear porque ele atrasará a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="bf40f-119">The implementation of `FunctionTailcall2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="bf40f-120">A implementação não deve tentar uma coleta de lixo, porque a pilha pode não estar em um estado de amigável para coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="bf40f-120">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="bf40f-121">Se você tentar uma coleta de lixo, tempo de execução será bloqueado até que `FunctionTailcall2` retorna.</span><span class="sxs-lookup"><span data-stu-id="bf40f-121">If a garbage collection is attempted, the runtime will block until `FunctionTailcall2` returns.</span></span>  
  
 <span data-ttu-id="bf40f-122">Além disso, o `FunctionTailcall2` função não deve chamar código gerenciado ou em qualquer causa de maneira uma alocação de memória gerenciada.</span><span class="sxs-lookup"><span data-stu-id="bf40f-122">Also, the `FunctionTailcall2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf40f-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bf40f-123">Requirements</span></span>  
 <span data-ttu-id="bf40f-124">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf40f-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf40f-125">**Cabeçalho:** Corprof. idl</span><span class="sxs-lookup"><span data-stu-id="bf40f-125">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="bf40f-126">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bf40f-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bf40f-127">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf40f-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf40f-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bf40f-128">See Also</span></span>  
 [<span data-ttu-id="bf40f-129">Função FunctionEnter2</span><span class="sxs-lookup"><span data-stu-id="bf40f-129">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 [<span data-ttu-id="bf40f-130">Função FunctionLeave2</span><span class="sxs-lookup"><span data-stu-id="bf40f-130">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 [<span data-ttu-id="bf40f-131">Método SetEnterLeaveFunctionHooks2</span><span class="sxs-lookup"><span data-stu-id="bf40f-131">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)  
 [<span data-ttu-id="bf40f-132">Criando perfil de funções estáticas globais</span><span class="sxs-lookup"><span data-stu-id="bf40f-132">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
