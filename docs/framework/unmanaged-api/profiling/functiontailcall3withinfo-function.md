---
title: "Função FunctionTailcall3WithInfo"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: FunctionTailcall3WithInfo
api_location: mscorwks.dll
api_type: COM
f1_keywords: FunctionTailcall3WithInfo
helpviewer_keywords: FunctionTailcall3WithInfo function [.NET Framework profiling]
ms.assetid: 46380fcc-0198-43ae-a1f5-2d4939425886
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4bd2bb56724f977d93e6ebff7d2c4c855a5a222b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="functiontailcall3withinfo-function"></a><span data-ttu-id="2bc4c-102">Função FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="2bc4c-102">FunctionTailcall3WithInfo Function</span></span>
<span data-ttu-id="2bc4c-103">Notifica o criador de perfil que a função atualmente em execução está prestes a realizar uma chamada tail para outra função e fornece um identificador que pode ser passado para o [ICorProfilerInfo3::GetFunctionTailcall3Info método](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md) para recuperar o quadro de pilhas.</span><span class="sxs-lookup"><span data-stu-id="2bc4c-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function, and provides a handle that can be passed to the [ICorProfilerInfo3::GetFunctionTailcall3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md) to retrieve the stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2bc4c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2bc4c-104">Syntax</span></span>  
  
```  
void __stdcall FunctionTailcall3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2bc4c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2bc4c-105">Parameters</span></span>  
 `functionIDOrClientID`  
 <span data-ttu-id="2bc4c-106">[in] O identificador da função atualmente em execução que está prestes a fazer uma cauda chamada.</span><span class="sxs-lookup"><span data-stu-id="2bc4c-106">[in] The identifier of the currently executing function that is about to make a tail call.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="2bc4c-107">[in] Um identificador opaco que representa informações sobre um determinado registro de ativação.</span><span class="sxs-lookup"><span data-stu-id="2bc4c-107">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="2bc4c-108">Esse identificador é válido somente durante o retorno de chamada para o qual ele é passado.</span><span class="sxs-lookup"><span data-stu-id="2bc4c-108">This handle is valid only during the callback to which it is passed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2bc4c-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="2bc4c-109">Remarks</span></span>  
 <span data-ttu-id="2bc4c-110">O `FunctionTailcall3WithInfo` método de retorno de chamada notifica o criador de perfil como funções são chamadas e permite que o criador de perfil usar o [ICorProfilerInfo3::GetFunctionTailcall3Info método](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md) para inspecionar o quadro de pilhas.</span><span class="sxs-lookup"><span data-stu-id="2bc4c-110">The `FunctionTailcall3WithInfo` callback method notifies the profiler as functions are called, and allows the profiler to use the [ICorProfilerInfo3::GetFunctionTailcall3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md) to inspect the stack frame.</span></span> <span data-ttu-id="2bc4c-111">Para acessar as informações do quadro de pilha, o `COR_PRF_ENABLE_FRAME_INFO` sinalizador deve ser definida.</span><span class="sxs-lookup"><span data-stu-id="2bc4c-111">To access stack frame information, the `COR_PRF_ENABLE_FRAME_INFO` flag has to be set.</span></span> <span data-ttu-id="2bc4c-112">O criador de perfil pode usar o [: SetEventMask método](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) para definir os sinalizadores de evento e, em seguida, use o [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo método](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) para registrar seu implementação dessa função.</span><span class="sxs-lookup"><span data-stu-id="2bc4c-112">The profiler can use the [ICorProfilerInfo::SetEventMask method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="2bc4c-113">O `FunctionTailcall3WithInfo` função é um retorno de chamada; você deve implementá-la.</span><span class="sxs-lookup"><span data-stu-id="2bc4c-113">The `FunctionTailcall3WithInfo` function is a callback; you must implement it.</span></span> <span data-ttu-id="2bc4c-114">A implementação deve usar o `__declspec(naked)` atributo de classe de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="2bc4c-114">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="2bc4c-115">O mecanismo de execução não salva quaisquer registros antes de chamar essa função.</span><span class="sxs-lookup"><span data-stu-id="2bc4c-115">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="2bc4c-116">Na entrada, você deve salvar todos os registros que você usa, incluindo aqueles na unidade de ponto flutuante (FPU).</span><span class="sxs-lookup"><span data-stu-id="2bc4c-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="2bc4c-117">Na saída, você deve restaurar a pilha por retirar desativar todos os parâmetros que foram empurrados pelo chamador.</span><span class="sxs-lookup"><span data-stu-id="2bc4c-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="2bc4c-118">A implementação de `FunctionTailcall3WithInfo` não devem bloquear, porque ele atrasará a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="2bc4c-118">The implementation of `FunctionTailcall3WithInfo` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="2bc4c-119">A implementação não deve tentar uma coleta de lixo, porque a pilha pode não estar em um estado de amigável para coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="2bc4c-119">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="2bc4c-120">Se você tentar uma coleta de lixo, tempo de execução será bloqueado até que `FunctionTailcall3WithInfo` retorna.</span><span class="sxs-lookup"><span data-stu-id="2bc4c-120">If a garbage collection is attempted, the runtime will block until `FunctionTailcall3WithInfo` returns.</span></span>  
  
 <span data-ttu-id="2bc4c-121">Além disso, a função FunctionTailcall3WithInfo não chamar código gerenciado ou fazer com que uma alocação de memória gerenciada de forma alguma.</span><span class="sxs-lookup"><span data-stu-id="2bc4c-121">Also, the FunctionTailcall3WithInfo function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2bc4c-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2bc4c-122">Requirements</span></span>  
 <span data-ttu-id="2bc4c-123">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2bc4c-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2bc4c-124">**Cabeçalho:** Corprof. idl</span><span class="sxs-lookup"><span data-stu-id="2bc4c-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="2bc4c-125">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2bc4c-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2bc4c-126">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2bc4c-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bc4c-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2bc4c-127">See Also</span></span>  
 [<span data-ttu-id="2bc4c-128">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="2bc4c-128">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)  
 [<span data-ttu-id="2bc4c-129">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="2bc4c-129">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)  
 [<span data-ttu-id="2bc4c-130">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="2bc4c-130">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)  
 [<span data-ttu-id="2bc4c-131">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="2bc4c-131">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)  
 [<span data-ttu-id="2bc4c-132">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="2bc4c-132">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 [<span data-ttu-id="2bc4c-133">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="2bc4c-133">SetEnterLeaveFunctionHooks3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)  
 [<span data-ttu-id="2bc4c-134">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="2bc4c-134">SetEnterLeaveFunctionHooks3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)  
 [<span data-ttu-id="2bc4c-135">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="2bc4c-135">SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)  
 [<span data-ttu-id="2bc4c-136">SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="2bc4c-136">SetFunctionIDMapper2</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)  
 [<span data-ttu-id="2bc4c-137">Criando perfil de funções estáticas globais</span><span class="sxs-lookup"><span data-stu-id="2bc4c-137">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
